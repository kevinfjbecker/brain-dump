# Android Netrunner Functions

* getIcebreakers
* getAbilities

* getIce
* getSubroutines

* canBreakIceType
* costToBreakSubroutines
* costToMatchStrength

## EXAMPLES

getAbilities(icebreaker)
getSubroutines(ice)

``` JavaScript
canBreakIceType({"ice":ice,"icebreaker":icebreaker})
costToBreakSubroutines({"ice":ice,"icebreaker":icebreaker})
costToMatchStrength({"ice":ice,"icebreaker":icebreaker})

d3.select('body').append('p').text(icebreaker.title + ' vs ' + ice.title);

d3.select('body').append('p').text('costToBreakSubroutines: ' + costToBreakSubroutines({"ice":ice,"icebreaker":icebreaker}));

d3.select('body').append('p').text('costToMatchStrength: ' +  costToMatchStrength({"ice":ice,"icebreaker":icebreaker}));

d3.select('body').selectAll('p')
    .data(getIcebreakers(data))
    .enter()
    .append('p')
    .text(function(d){
        return d.title;
    });
```
