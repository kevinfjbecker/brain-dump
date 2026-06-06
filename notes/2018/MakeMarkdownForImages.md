# Make markdown for images

## Prompt

Could you wrte me a PowerShell script to take a list of png images and create markdown files?

Each markdown file should display a single image.

The markdown filenames should comform to the image filenames. The image filenames are in the format ```{name}_{yyyymmdd}_{nn}```, which is the name of artist, the date it was created and a two-digit number with leading zero.

The (h1 #) title of the mardown should be artist name and the formatted date. Please use Norwegian formatting for the date.

## ChatGPT Code

``` PowerShell
# Folder containing PNG images
$ImageFolder = "."
# Folder where markdown files will be created
$OutputFolder = "."

Get-ChildItem -Path $ImageFolder -Filter "*.png" | ForEach-Object {

    $file = $_
    $baseName = [System.IO.Path]::GetFileNameWithoutExtension($file.Name)

    # Match filename pattern: artist_yyyymmdd_nn
    if ($baseName -match "^(?<artist>.+)_(?<date>\d{8})_(?<num>\d{2})$") {

        $artist = $matches.artist
        $dateRaw = $matches.date

        # Parse date
        $date = [datetime]::ParseExact($dateRaw, "yyyyMMdd", $null)

        # Norwegian date format: dd.MM.yyyy
        $dateFormatted = $date.ToString("dd.MM.yyyy")

        # Title
        $title = "# $artist - $dateFormatted"

        # Markdown content
        $markdown = @"
$title

![${artist}]($($file.Name))
"@

        # Markdown filename
        $mdPath = Join-Path $OutputFolder ($baseName + ".md")

        $markdown | Set-Content -Path $mdPath -Encoding UTF8

        Write-Host "Created $mdPath"
    }
    else {
        Write-Warning "Skipping file with unexpected format: $($file.Name)"
    }
}
```
