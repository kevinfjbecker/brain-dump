# Quick Rank

find everything that interacts with deck

thought: card { card: data }

## Goals

* tooltips
* hightlighting cards from charts
* hightlighting charts from cards
* fix sorting

thought: could deck be abstracted and expose a similar api to an array

## code notes

``` JavaScript
d3.selectAll('rect').on('mouseover', function(d){ console.log(d) });
d3.selectAll('.card').on('mouseover', function(d){ console.log(d) });
```
