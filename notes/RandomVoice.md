# Random Voice

| Aspect          | Trope A | Trope B   |
| ---             | ---     | ---       |
| Weight          | Light   | Strong    |
| Spacial Quality | Direct  | Indirect  |
| Timing          | Sudden  | Sustained |

``` JavaScript
const aspects = [
    'weight',
    'spacial',
    'timing'
]

const voiceComponentsNames = {
    'Light-Direct-Sudden': 'Dabbing',
    'Light-Direct-Sustained': 'Gliding',
    'Light-Indirect-Sudden': 'Flicking',
    'Light-Indirect-Sustained': 'Floating',
    'Strong-Direct-Sudden': 'Thrusting',
    'Strong-Direct-Sustained': 'Pressing',
    'Strong-Indirect-Sudden': 'Slashing',
    'Strong-Indirect-Sustained': 'Wringing'
}

const voices = Object.entries(voiceComponentsNames)
    .map(([componentsString, name]) =>
    {
        const voice = { name }
        componentsString.split('-').forEach((component, index) =>
        {
            voice[aspects[index]] = component
        })
        return voice
    })

const randomVoice = voices[Math.floor(Math.random() * voices.length)]

console.log(randomVoice)
```
