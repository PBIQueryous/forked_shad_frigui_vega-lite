﻿## Intro
The Vega-Lite [ecosystem](https://vega.github.io/vega-lite/ecosystem.html) is huge, and there are many integrations, applications, and extensions of the Vega-Lite language and compiler. Here's a quick overview of *some* of the tools that you can use to write Vega-Lite specifications: 
- You can use the [online editor](https://vega.github.io/editor/#/custom/vega-lite) to replicate graphics from the [example gallery](https://vega.github.io/vega-lite/examples/) and make small changes. It's very useful for learning and experimenting without the need to install anything. Including data [inline](https://vega.github.io/vega-lite/docs/data.html#inline) in the online editor is okay for small datasets; but if your data is large, the editor would have to do a lot more work slowing everything down. Uploading data somewhere and accessing it via a [URL](https://vega.github.io/vega-lite/docs/data.html#url) is another option but can be slower for large datasets, and you will not want to make your sensitive data publicly available.
- To overcome the limitations of the online editor, you can use VS Code + the [Vega Viewer extension](https://github.com/RandomFractals/vscode-vega-viewer) to work on Vega-Lite projects locally. The Vega Viewer extension provides language support and Interactive Preview of Vega/Vega-Lite graphs and allows you to work with local files (more details [here](https://github.com/RandomFractals/vscode-vega-viewer)). Additionally, you get all VS Code features.
- If you're authoring Power BI reports, you can use the Power BI custom visual, [Deneb](https://deneb-viz.github.io/), to write Vega-Lite specs in Power BI and benefit from the power of both tools. One Deneb-only feature I like is the ability to use zoom controls to zoom in and out in the preview area. This is very useful when working with large graphs.
- If you prefer working with Python instead of the JSON-based Vega-Lite language, you can use [Altair](https://altair-viz.github.io/), which is a declarative statistical visualization library for Python. Altair provides a friendly Python API that generates Vega-Lite specifications in JSON format. Environments such as Jupyter Notebooks, JupyterLab, and Colab can then take this specification and render it directly in the web browser.


I’ll try to add 3 JSON files (if possible) for each visual: one for working in the online editor (```filename-online-editor.json```), another one to import it as a Deneb template (```filename-deneb.json```), and the last one for working in VS Code locally (```filename.vl.json```).

#### Note
~~I'm currently not configuring visualizations' themes *separately* in the [Config](https://vega.github.io/vega-lite/docs/config.html) object. I'll revisit the code to do that.~~
I updated all the files to separate theme customizations in the Config object. I added copies of Deneb templates to a separate directory for quick access.

<br />
<br />
<br />

## W.E.B Du Bois Challenge 2022 - Graph 3
My first Vega-Lite exploration was recreating a W.E.B Du Bois [graphic](https://github.com/ajstarks/dubois-data-portraits/tree/master/challenge/2022/challenge03), which is part of the [Du Bois Visualization Challenge: 2022](https://github.com/ajstarks/dubois-data-portraits/tree/master/challenge/2022). I used VS Code as I can't add TOPOJSON files to the Power BI custom visual, Deneb. There are workarounds, but I prefer working with VS Code for [geoshape](https://vega.github.io/vega-lite/docs/geoshape.html)-based, Vega-Lite experimentations as it is quicker to pass in local files. [Open the graph in the online editor](https://vega.github.io/editor/#/url/vega-lite/N4IgJAzgxgFgpgWwIYgFwhgF0wBwqgegIDc4BzJAOjIEtMYBXAI0poHsDp5kTykBaADZ04JAKyUAVhDYA7EABoQxKHKhJMaANqgA7jQAm9NADYxABiXwaZLGgAcAdkshMdQXDShMcAB6bULRAAJQBRABkAQQAVAEkANVCAAgA5UIBxYIB5JIAFLNyAVSi4rJSkrIAxJOiACWSAZWiY0IaK6rrQxRBClNjo0IARJKaWhsoQAF0lADM5AJAEOTYIHCQoT1n5hpoAL09UAGYAJgBfJQMNFFRQBgAnQTQQS8wkAgYIfgBGcwQpGXkWzuyAC3gAnjgDq42Dg2NI5N0ZnANPcoRBXj4ICBTudXHckLIIHNgdpQII2GwANYMHBPQyIu5sBBeZ5XFnEJCCBhwLGBUD01BfJTojRQyKCJBMJDIboinxJSVMO5wYg0DTseToSLhbqwnAMCVuBHoEzmSxm8xJfhJRwWBQW7EKfkGNBfY7CjFQyrku6GFAe0UKphKlVqo2akCVHVKPUG9XGkA-c1mq1JY5m+1mx3OtBiAM+J6RO6UgkQJBY-NwIMh1XxiORYK6mFx8NPQ4Zi2pizJ8zZkACkyVp4AYU5NGJsjVss91eVtdb6GHkSb+sNGqeP0zlutxzzDvOOdQAE4h4u5LI4FA3FAGJpK7PQ3WR9EVy31+hN52d3uswf+y7BRPEA5ShWI2F0f1gJnRU5zDd8QFiZcY2bNcE0-FNvy3PsBQAFlPEAiz2ORIJAh953gyIAC1X1QiNekGUJglTdDez-AV7Hw4c2B9JADDYadAxgx8FxAYcshop90HoxjmJ7bCAK+QcoNFJ5YkuGB+PvITyITWJBgkkTpKY60WPk10XBAp5BjgCUIOVAT5W0uCEwYgz4N3LcuzktiFMOfD0jgNg7loEjoODWDJJAdIkJAWNaKeW0e1SDJslaJJIhSYYskSRsfNdRx8NiQRhFkNgaArZTHPC4T4NiaNYpQyK7S-JIkywvLBQ4yrQNkAw1VkULBOqnSI1iFI3ITDyWua38nX-NB03wgBpUtywcqsnMipaGgmiMpowpIZtYuaBWOIVuqeJa4FkTAGCgSkwXWsjnIjJaAE1dqedMkutdtvJOgDjndC70HCNgGHK-rBqqmsXqeKJPvQbtPOtU1-sPDyQZAABZcsy1gD44GwCrSM2kTsZiuLIpY1N9uOjG8Kx3G7jBCVeqesn4Ox-TkNXSLvpRpI-vagGFr8pmkBoC8OeGuH0GxrpebfBMjNkkWMaUyz5ZoWAbAJGXYci7HYkRxMfrTH96fm1BjgKpmpYvGRXgNiLyfGpX4qkzKZJM9HreOICtZx8qZHuGgXZqhNsfEj3qY7A6Bf3UWba6oPsZDjOcBwcOtNlo2dtjkS0cFxL1et9t8Ox+YCWhja8-Jl9C-g1XfbLgVDjtoOUiC+gklHRkStr57IpSYdTeRlri6Tw9DlTz0nm7u5e8GJBKTYZ3c8NkTMtNlvWr99vzq7uAlXLEsI5GhfFYavnDO94z97bgDDnF4-dCSWppTwGAaHszfXfgikWou975q2nuXYGx8OSXAvnLEAKR4ggIYg-UyHVDiMzfkkAAUnAO4EA4CPX-pHCMKQsGmzpl5J+aBDh5ixikOA79sZ+B1ppbqw9t7YyQT7R+4D26a3nugeh783pBUpLAkeH0m4JiOrJA+z9A4CJAFkH+rDSb13glkYBUiIwyN9nItAOELKKKyJSCUGkZREMvugLIS0uEoP0agHCR9jHKjIAiSxcCsiNm0U8PeqDk44UgYo3I11CSsw5JOIenMEy5Epo1ESbUWqJ1moeHCGDFHBA0gYKssQIBsxdB4yKwQTY+K9sgsBKTrY4VoUHBo4Ne7924lLKJ6iEwNDHqUkAU8Dql14QBHC-CVLoDqbeGASQV5rw3mw6JEYGg8xvsrOioDW59IMZ3RR0RQk8nwZsaZrSIzRHdgsz2IBhbTXjlbXCc8hkgE2b4NahSRLRAABqmzOQdCelTcIKJuYUV4MBxGGUbscyKfiHFiGcTc+Iv9aCRMBfBeIcTb7wW6duG0R0zKoDtFjeIuClg3XhQmeIwKqZ33KSsr5AExCv0UQAdXLD-WQZBMDuL2VveCtKkWLN8csnhlLczpJubSnkmAkjQuClLKcjyOWIM6RQ60GKOpiBqXS8qqhCRS0JRGWlJSQVku4f4w8YhBkFnQLSsETIpZkC1U8Wlki9XN15agyYuJKQELpAUkAMwaA2QMLyIIlkfEur-N6wQPg7gslKqCL1PrBAAXmkoOQcAsgzG0O6L4QovhiGDacaYiwkDFhZJgCEUIyCBQgDAJAkJHQgGuqoPqTKWSqB9Cyb1vqnikvXEoYt1b0ClQQM0x4wp1AeBZHxZAmrAggF6SmNImQshpQyllHK3RUWphnb2JQny0Wou6O8tF27ujJLRfu7oiSE4XO6Lo-ecklDysOres2gs6bdDBVhPN+ImUHCCAAYgzUmDpIAf1HnMI4AAQiYRw3RgNfHsGIRwXxoMmHQfYE40HDgmFg2II80Hhw4UiGIew18f2DBOGINJ0HBiDEiCYI8YHoOhDEJEQxJhKOHGHIcSIy5g3dopGGmgtI+QxvbegQNrgS1PH7YO7obhMCjuGfPENsb42dtZT2qEUmBpDtcO4KEuR4nrlzTiOasn5OgAML4NA-B7AuAMI9QU2KCSwCCk8EUS8ZN+ACL+wYDAwNlQgMOStxVrplvTEDbo6R8Q4B-lAVASQAACFbeIzF9GQCGUwtgEuGeQNgVZCi6rmDdHY+xXTi0K5gYVNg7DoGELYcN3QSpwFqHAKrAR0y4mQIW9APh-DYjzeq711qbixV4g2ob3gYTUJcEwdeLLmSChcB4GYARsWpeqxYXEUp7pkEZAwdm6ASOhGHJUMDlQGvkGugBUAQUfVZZAKVaWSgPBlt6q81AZgnsXd6h9d7zglDNoYAgQkC1-vcUB7IXIo2rUOBcIyXQkODBjam8KMECAZuCGiBJ0TABHBgBbdkQFR+j4rBwbMWSJ9xBomBGRutpYYYwqBzCUFoRKJgNkU0zHwQETcIBWc2UqPMJ4qgw64KSBeXQDXJT8+2HsA4WantS8EOEGgA62vYtMwcWQBpBC4jLSsStvbQDohp1CJgEp7rThN3TowALGfM9xDgRkkhLwLnBL2kAnI2d4MKGWbEOIgA).
<br />
<br />
<p align="center">
  <img src="https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/du-bois-challenge-2022/resized-graphs/graph-3-original-resized.jpg" />   <img src="https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/du-bois-challenge-2022/resized-graphs/graph-3-recreated-resized.png" />
</p>
<br />
<br />
<br />

## Black American Population in the U.S.
I wanted to experiment more with Vega-Lite's geoshape mark and decided to do a choropleth map with a dark background. Choropleth maps are great for showing the big picture and helping readers recognize patterns in the data. You can easily see that the highest concentration of Black Americans (alone) population is in the South. I added tooltips to help readers access exact values for each county. I used VS Code.
<br />
<br />
![](https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/2020-us-black-population/2020-us-black-population.png)
<br />
##### Note
In 2015, Shannon County, South Dakota (FIPS 46113) was renamed Oglala Lakota County (FIPS 46102). The [2020-us-black-population-data](https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/2020-us-black-population/2020-us-black-population-data.csv) has this change reflected whereas the TOPOJSON file, [us-10m.json](https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/2020-us-black-population/us-10m.json), has not. I replaced the FIPS code 46102 with the old one, 46113, in the population data.
<br />
<br />
<br />

## Premier League 2021-22 Current vs Predicted End-of-Seasons-Positions
I used Deneb + Power BI. Here's the graphic that you get if you [open it in the online editor](https://vega.github.io/editor/#/url/vega-lite/N4IgJAzgxgFgpgWwIYgFwhgF0wBwqgegIDc4BzJAOjIEtMYBXAI0poHsDp5kTykBaADZ04JAKyUAVhDYA7EABoQAdxoATemgDsABh1L4NMlm16lapJhSpQxJIIZwIaANqgAKnCQI0IALJIsgAEAMJ0AJ6KICEMAE6xcLKYaACMSgAKCWo0UJjs8qgpAL4KHl4+6AAyNKSxOGxsglEx8YnJqABMGVk5eXJoHSVl3r4h8IIQXs1xCUloAMzdcNm5+QtDIJ4j6ACCsZOy9tOtc6gALEsrfQVaG1sV-oFBAKqyImrHs+1il71r53dyr4AOpOTBBAASIyULS+aAAbL9Vv1UABOQHbTZsbCJGDQ6IzNraJHXBEYh7AxqkZwwwmnAAcJP+KUGpU2QPQAGU2Ax6N4cJh+rSTu1UUyUSl5uTRrFwhArIIgul7EgoHBPkTCvoQJlln8JWJpbt5XIggA1GiCQQoYVwwppHU9ZEFelGkCVOA5MFwWIa04s8UFQ1s+6+ABCsSMWCFBJFqUWjr1ztS8LdADk4MooEh5YJ1bbNSkLomrsyzm6I20AGZsWIfAv+n4l-UFFLokMc91wZY02N2lKI5vJ+1ugCitUF8gb7RSWkDqR0FbisjzkWnqUZQ9JhVdHcxwMsNbrfpnYq3-w6i73DzTtdUsBPA21utLEtuAF0SiBElA2NlZGQaCgAAHkBIBVjQcCCB86ChkomDhDg6roLIbAIDQhxNEoMixO0oAQVBMF9kSRSkUo1rhD6rigMgsQANZgQhSG+EwSC+kov6CLWYFwMBOC+ugFiYAwCAuAA5LCbRie+QQADxBEJIniS+LbSUEAD8QRiQAxAAYvMZxFvCYlBKgWnafSKQhEWuliSAZHfrIv7-oBNggJEbkEdBox0sk8GIchIAAI4MIEeRWHkpBRDh7QgGoThqrILn2Uo4QdGBXlESpyakRstEMW5TGBVANCxFAebRTQABeyFiGYICcdxbm8fxviKaJEm+Wp8ntcpTrXGpmk6fphlnMZpnmZZ1lnLZ9lfj+f4Ya5oAefhkHeeg2Wkv5zHoCFYV0JYNTqrlbL5YxAW+CVZUVdh1XIfC9WNQJIDafMAAibZiGGKWOc5S1gat4HrURklzDtgX7Ukh2RSdZE0WxBWgEVviYLxfnuQA8lWVaTHh358S9vWdSK3UKZYSliVt+SDUEKQTTov01kknL3akXQNY0TWgC1RMUx1YOYGTxPU3ItNicoMAiCZZliUw1pQHRdkOQtyVuUDmW+KLU4gCje2hdDEXHb9aPAfjmubf1aynQj9EXbtuvo1EzOYKzNXxhxXMvZLIi-arAPqxlIM+XGEO+FD4VHVFX6m+bwfoILc1FO+nuyBBy0gDgSBqGryNsDgaB1UoTDYoKFRFyAeZVu0l5KJGxg11eICsYrZCxDySW+D7aNRMQkHKGB8rt3RgWYLEgQQFncJfi7vicuQbBwC8ACSURIMBNAQAAGmBtaQacuv51EbfqGgY+OEoJ9qJjWclQhqTmGhSAYWgVb2JM8E5HRzioG-ExwORJATAoLKhzgHWulcgFQV0nIV2bNCgJnChVVAsgGBWi-OvTeABNMC2QIBAOQefOAX5WICVAKoDQMBUjBgaqVcqyFQD51VBEVIuUgA):
<br />
<br />
<p align="center">
  <img src="https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/premier-league-predictions/premier-league-predictions-online-editor.png" />
</p>
<br />
<br />

I increased the ```labelPadding``` property for the ```x``` axis to make room for a Power BI matrix visual. Here's the final graphic:

<br />
<br />

![](https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/premier-league-predictions/premier-league-predictions-power-bi.png)
<br />
<br />
<br />

## W.E.B Du Bois Challenge 2022 - Graph 7
Since I started exploring Vega-Lite, I quickly realized that recreating visuals is the best way to learn. So I decided to recreate W.E.B Du Bois Challenge [N°7](https://github.com/ajstarks/dubois-data-portraits/tree/master/challenge/2022/challenge07). [Open the graph in the online editor](https://vega.github.io/editor/#/url/vega-lite/N4IgJAzgxgFgpgWwIYgFwhgF0wBwqgegIDc4BzJAOjIEtMYBXAI0poHsDp5kTykBaADZ04JAKyUAVhDYA7EABoQAEySYUqUMSSCGcCGgDaoAOJxZyuACc0IALI64ikAEEycAAQmrbBjlsADPwAjGLODlZ0Oh4AyuqYDAboMTSyZIJOSgAK1lDm6u5owQEBSnYxAJIAIkUAvgqm5pY26A4Zzm6e3r7+6KH8AEwB4UiR6oKx8Ym2KWnt2bn5SIWoAJyrlGJllTWowfWNFta2bZmu7l4+foEhYWWjURNxatOto5Fwys45VnmyBU5UKV7Ds0AMDiAzEcWvZHB0Lt1ruggqERmNos8EkkQAB1GjKNgAd0+30W-2WgOB5WqaAAzBCoc0TnClJ1Lj1bP0hmjHpMXtiIh8vgtfksVgFNtsaahwQ1IU1jm95uculdeiAucN7uinlNsXiCcThSAfn8AWgqaDUPS5YzFbDlWzEeqhoM7rCdXysTNUukzqaxYCAGwADilu32toVMNO8NVHPQroG7oivMxrw9QtJovJK1pwUlIOlssOTKVZydatsSZTD3GXozBqJJJFZopFsL1N2NtL9tjrIRVcTYn4tK1HrTep9c39ZPN1st0sjvZjLJV7KRIGTo-Hqfr6YF7xoLZNc-bqCDq3DYIZ0eZjsHCa3I7HPP3U-QTaN2bbK2C1+tW9oXvCtH03MdR1rT0D2nP0f0DMFFwjICywdUD43AoJaSgyd+WZKws1bBDUAAdjDItdhLeVgPLOMN3VCDsLfDEP1xfFm2NANc0BAYAJ7ajUP7ddnVsbD+AAFhw988OSX1lS4+dyK7OooxotC6JE9AxMk5jdRkzNj04s8VhDIMAKou1VwfDCGJHHTtVw71P3Y78iO4tAzIoukUL7NdKyfST+DEKSWP02Y4Lc+dPOUvYfKs9D6NsQLgt0htDwIwz4Pc1BTPMuKQI0ocQGSkK9KctjDRPBTzyUq1+MsgqBxs2xgv4INSrS2D5OMwFxIA5cBN86zEvQVr2tSmC3gyqqerQEMti8mV8topqRpAMaOsmiqOKy+dgn-Rb6rvFbhKKgB5UgrA8caHOk8rwu6nN5z6xaBoak7-M3C7rGuzbWMFTLIvPEjoqtCzjvU1bNJAb6rpuic7sbFyZqe88hj45aQAAMUQPywPVFE-rCuTZ1Rv8Sn6zGceQYbocJib-qPFHf0pPLVNQ6m8ea5FbgZ-Sv2Z4ikO89n7U52mis1Pn7pJ3aapemK3oh8WEuhqXbtC8qAcF7LglB4sqdxiWn3VhHNaRyqjLJ1nDsNmnVaKmtpYzB7SZZulaqXO2ubWp2NbKjNtat93UDET3KO943Nz9s2A-1ZHg+IhW6sjh2n23V9-c62SZzlv9w5UldbBVwr05fXc63N9LCNPa20BI5ODdFmES6hx3y+d+PLbzwEC8A5vi6NtPMMgzuurd4jgl417U9LkemKzrag57+u+-BtTW9Op9GKJ8qBcT3Xhf7ov0E3z7bIk3eXdloGTMpgfT6HueL-s2Ps4MnX5xBtmT+xp+2+3nZK+Xcdq30BHrDGD8-722fklEcKVF6sVdivC899f5n3xnAoKwD8I12qisIM+sI5QIwdzYq8CcHOW7mAsEfcjob3-lvTcG0x45wirXEOjdkIkMYefFqI54Z7irrgwGHDiJiGnjFdeHNeGYNGgIyh21XJiOyuJLhIt0GyLIbDX6rCQDIJoagdRsUeEwIAV9S6ujEH6WXoYscP9Boty0WtHRgjK5x1sPvFBhCMYAF16ggGIFAOQUA1BGFAISfE9B65iGBJgOg7RNAgEwHAAAHpgWwABhOQkgGAUAmMEiwdB2CyA8GwAAZh4FwCBrA0FCaUgAcuQHw+gPBICgMEqwyhfQeEwGwNpFwcC1LYMoCAlBnDlLkBk9A2SrAUBsEoSZ-wUgAC8eLTyWZgHEcAaBkCwLYYQeyUkLJABAZg8TMAZCyEgZQ3S0hggWmcpgFzEmGBANkop8S5AeEKbk-JnhLAQA8A0gAF2QKwrTqkAEvIj1KBUgBgHgcBsFSJgDwlgPDED0OizwggADkAAj9w4ylBVDkJ4JgABPKplykDkg8AAVVkDQS6EA6CUvGb4pQTyXlwCxlMrJbA5mjGcDyhJfKpmrPAY8854r+X-G2bs-Z6BDlYGONy2Vly4AABlUhwAABI7KOXSMQATkBWAANa2BSekkAEJCmhOmcYEAkTlDROtCRBa8AlXTM9XE8VaBQAVPKRAOA0z+BXmSWk6Z9gXDaoAKIxBJSATZthOiyCgNSrGAAhCZkqaBrKKKsAJggkCUsVM6zAVg6UQEmVYBA4SU00EEMcwNTa4CCC+OgBqSg4AAEcGA6AKrUWoXKQDmqtUkzAlKhm2CYCKgJ5hgl3LIG21JbbynHk7bYfBZxp2zvQAOulFy1AsrODIKwMbAV-BXc4JAqSaBJFAKWpgHazrlJDWGttaScAwlUAkBAlBtC6E8AAXlAx4YoAQPAAH4PBtQ8KgDwwwR0BMpRurdXamH+CUPuwEIAhV3KHdyoVV79A3t9KK0JiTQA4BuSuioshZCKgCAE+9j6228oABpoB3COpQwTBBCowx2rDylcMzvw4R1IxHTnUcBKAAkyBUhGH-LxWkY7q1pEBG8gAxCUcSVQXBBmcLpzJIYAjZtpCRUzwQsYhmTCZ-xSgMjuAsGgWQDBBCCFQ3Kf9GgtA6D0EkYwo6zWjEnaAPD1ro13tztaYouHYvJAqA0kwCa83-DTW5zNHgc2ZcwFKh5iypmKuNegJgbBO3HEXRmkZlGknrqScBvQYJxKsaUOh5rQXgzWd84ptQAXAk9ZC8AMLSgJ2cckzF21Sg6VwQS3E5LsaABKK2KjxpqCVrL6B025fy9twrBaeILU2WV5VIBKvVZsLV5dDXQBNcCyBoo7U0Ntpa4CWkkl+sqEG+9kb4Txvjoi1Ng9UbZsgHm4kgYqwlu2s-NUM6OJNsFey0urNubDtFZlMCM7RqLtXaZLd+r9zGv-eezKU1nXyetZyqakdzmIlRJgHST1ShvXlb9bhgNSTg2hvDZGm1MasbxrsHGxNybU27Zyxjgr2PgjFpc2WitUWtO1qFQ21AzrN0tsVKATdonbA9pAP2wdghB4wIZxNkHU7psVYXb2urt6ydJIN9u9Au7nDRcPYO-4UR4mkDvQ+p9IAX1vo-fz79qTf22H-QwQDH2PDgcgyUWDHgSKIeQ3a-jIAuv68w2jxKEmwfSdkLJi9ZHoBNEo9y+Tba6O3N9Ix5jLQOuQ+D22oVx4dsgEiMa7nWqeMLhz4J4TruC+tFBMXqTXSZPm9r3CJJSmkAqa12phQGmlBaZWHpgzRmTNKDMxZqzNnD92Yc2IJzJbyBNA815nz-GBvqBp-oQHzngeWtB-hoXcWFuxKS-DvoqlulvGqjtLujnlpjimvmoWpTodudjGoTjVo7ndqTg9i-kUGOG9t1hTkGNhD9v5i-qNkDpNrbmDj-nNvFv-uDjGmLmthtlttAT3ntrLljsdsVkwVsvjogVVkTigSTqui7k9rTkMG3nnsNhTl9qxo-r9s-jgcFm-uFp-mQd-rFpQQtiRHDjGjiIjsjowVLiqBmqwZwdjujJwQgXOrwcgSbk7vdiAI9hIbTl9lTrnhgXsLEqhv4ozskjzopk1rSEGCRAATGlkPGith4JkvGg0gACpJpgGGH7ZQGbLy5BhKGTo0F2pygc7KoLS8ptrKBNZBTAh0qwBj6nLqCXpe7JZ6ZVAMDZoooQCZIwA6AZDaZDADADDODeBIA4AwB1JIYAACEAzRyg5SfeDANAIAY6BhMQ5AbAngDKFQcu7BewtI8B3BByPq6qoeeqhqPqiEaRM2GSo6Amcgm6ghtG9GdhfSvQ7WLmcA5S0yZhfeyqQwAS86UAFq4Kvg7m6AumVQ2aVQwQmSnRc2HeSS4K+I2SQmMITApanxXudSFqSQ5SOgoaSur6gg8qMaLBkBzgYeWJpWGxFWVhN2YJj6XGAAir7iegHgpiAJCcoGdHRlAOylHjHugAABRx4J49YeAACkKeAAlEnhBtBnBhKLSJnhKMEJkT4Z8dkgwDttQQSdco3qTtPASfGtHjCNyS8LySBgKcKaKchmnjyUBnyUhniniviUgJidifLmsaHnaR2tCWPqAD+n+vqRaYacnuKR4NaZnninCe0hajaQEnkagJ5t5koCsqkJYE1pGO3o+gAJpVCPpQAQopJtqMloBVp6Dc6fHZp0pYbRr5DOCMnMntJslAiUBOmqlXGk6JbOmYnvqfrhpmEEkOkrEQI+FappomAS6IlaouDxb+paoplFAvS8rYlo5GF4kD4ZDdmwGhCLkSoKrEmXaknOBxlHCJkBIOphJJIQAskNYhCoZAA).
<br />
<br />
<p align="center">
  <img src="https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/du-bois-challenge-2022/resized-graphs/graph-7-original-resized.jpg" />   <img src="https://github.com/shadfrigui/vega-lite/blob/b7cb5cd2d4ccffe43612b2485d80965b7d231f31/du-bois-challenge-2022/resized-graphs/graph-7-recreated-resized.png" />
</p>
<br />
<br />
<br />

## Monthly Variance Analysis
The following graphic shows monthly actuals and forecasts in a lipstick column chart along with the variance in a column chart. The code is optimized to show millions/billions in the Y-axis as well as in the tooltip. Cross-filtering is also enabled (Power BI). [Open the graph in the online editor](https://vega.github.io/editor/#/url/vega-lite/N4IgJAzgxgFgpgWwIYgFwhgF0wBwqgegIDc4BzJAOjIEtMYBXAI0poHsDp5kTykBaADZ04JAKyUAVhDYA7EABoQAEySYUqUMSSCGcCGgDaoALJz6aEACkk8pWdn0ABADkGCJnABOaAIxKAMTYvOCgkCEw0ACYAFl8ADgA2AGYUyiixJQBBKEwGHT8AdjF4koAGGMoY+KUANSQvGlsoOCcABW8WxyQyODR+MvTCqIBOAF8FU3MYSwC4JkUQB2c3D29owODQ8MjUKLKysULEqPj0xOzc-ME-EcT4kZiR3yq6hqbZFvbOuG7e-sGZQSMQmU0cM3QJgai2WMFc7k8PlQyU2ITCEWivixUUKD0oNRAOTyBT2vkSiTJJUoKJA9UazVaHS8XXU-1QgKiiVBS2mliyOB89mm8LWSJiqO2GL2h2KZTulEShUuxJuqF8IxGcuS1QVUTe9M+jJ+fz6qAGlDKyVi3NhlihAE8YcLVoi0JkQEE0TtbjExIrCoVKHdlddMSNkskjlF0v5ae8Gd9mb9WabBr4cckbbz0FYGHYeeCRa7UBcPVt0bt9o94tVA7GiaG9vtUuGRgrxXGDV8mSyeqmLWIolnwZZczchYWXetUEqy16pftcSlFek9YSriSogkgXczgl9R9u8aU2hAdVxpMCxZ0FkGGQnZOEdOCZ7Jbt1WV4gHLZRCh2G5uhw1qcgZAgeCY9smfanhauIgpetroAAynAOAPisT5IiMEoVrcowHJyQb1huqpbjEiRiCMX4KthnaHkaSYmjB2LxMO14gAA8rk6FwlOSK+GUOHemqjwxKM8TRvEBIAaRn6JI8ySDMkBJ0vRia9mygKFNqbEQiALhsMQPFFtOWJCVKCQjCU2nJOktEyZi8S+DEf5tuS4GGupUGaZQvhiGUXIIdmIAACKhMZfF+Gur64SJymxE8VSlg5exOcMvptp+HlHoxJ7slUYiRmMAC6EwgJgXi2BAABmwQIEYoBhIIUAMIIaimiAIQ4G1LQABS1V4yCYL1qh5AghgAOQyRNxUKE4E3pBAE0AJRzRNADiE1rQAQitizhHyJEACpsGwgiYDQaHck1LVtZgHVdT1cD9XVagjWo7iTTFOwzWti0rWtm07XtSgHeg30RCdZ0XVds0gMQUByGEuzGCAADuNDKNeiQHEo8A0GQWDRLjIC-Ijyg0LI96aCAAAeaCgNVNBwIIyh2rySiYPaOAdbIbAIJTBRKDIXi7IzzOs+zj6iosbBoegEDuCAZVILTNAGDTwTM44liYHLytlY6NNMyzbPoKpEHHtBnPcx1ACO+SOHQag0KQ+1qxrjOvbsIC+QApIsZCNMoADCZ3BAzpO0wKlije4lDaLorQALzJ04ZROAA-PNADEIVRCHWQh74E1OKg80TcrShtZ4ghh4IEfoAbZVtfa06o8gXgANaR1zPOWEw0JKBjWMQn5SiIw3SKgHA0dIioH3jRNFueZBJozU4AB86dZ7nUTbUkIfJKX5cTXn22JFk8S7c3l6dz3NN9w9oSREo9ocdV1UQHAYtRzH6BxyXivHKGk4Ab23hnbO-A-JlycH5W+oB7691trrWer8QDv0-t-X+s9-4LzGpNYBDFQHgJ3lA5ysCyQGyUGTNgFMqa9zQZHE2ktzbxlXlbf4SgBpDUsP7ZupVLwj2xiTfGhNKz+RoZ8OhlNqagHpsbCWZsrwzBtv3dAfMBayCFiAEWv8WHKNhCZHwYxDaR1VurZh3s+FRAMNXJAtcACic9LCPSQH1QBlAa4s0Blteau1lqB2DvXRuIA84FyLr4IJmMOI4HcXQI2gx3TeLruHaef956eMTnoJwqcyEV1gWfHGYhHFiBDpXUxZVJ6N1AIA2Y5ZvTCyaqaWp-MkCUyMHON8iwHJKDaGwCATgiGLBcOQIZ7CWggDhpVKmppDBhPzoXYuiwc6+EcTERxUkVn70PskFZIUL5X22lMyp9i25Ig7g0B+oAn4DyHujTG15FJlVofQuRGDmFKPqfOdBtz0AO1sBddQF03ZlT1tDS6DUQAGKlhYbkMLwYNMhqdc6kLOZ0EEB1CGkQSqmLvlc5B6iQCD0FA80efh3QRC8GwLuHU0YwBEIsKlNK4CxPiVzGChQXnSLeZHI24tTaHRVIsP5IAAVO2Ba7PoVS0mRzqTeEiVdyoophlChFKiq4CtYeuFUUNUVoXRZgTFQrQy4txXDRGsgmbvMHlALuQc2B5mUTnAIji3WOLKIsYgzM0aR2ZbS3WMyIBxJCDrMqtUdbIXIGwVoABVAAku7SxNMUlBEcEhGgAAvU0ZlyoYtNLIVqggVYewABpyraZTEJ89wlLKiUoIOmM0DVR0N-dFdrq2WFrZExYKSshU2Neyextc2hIGULy1AySHEs07egHOxTSkhyVRYiAJ15agDYFgn+0QxAlvVttNg2B+a9xoHa7athlFoOTCK09XcM3Zr8GUPdEAACakctbXvQI0cRixlCVvkKgFtgg215rtRrIDIGLodsdZGqdI6x0ToEi3cgvwzYbsaJ+kAfNZB9CUBTNEF05CWBgFrTN5gdGYt6LIZQ5aRKCRAJR1Db7pT0YgPaDwZ0jooIVgCkITL2NMDOvenN+xhYCaExVFls7ypBpDde4dLM02YGE34WMKTpM5xiBGCS8QlUkt7iqyFqAKp6DKgRyOwiISRjxnAAmRM1SzkRl4HDXgABKY6aAMA1h2f1HV52HEXUyyTtKADqjyIRKQnrKpuYKmE02qTWrT8VdPcPMCptUvgZWfDUH6uJUBZFoBiE+0xQA).
<br />
<br />
<p align="center">
  <img src="https://github.com/shadfrigui/vega-lite/blob/0f799574ec0d86ac9a16887fea5685e25caa1ee4/monthly-variance-analysis/monthly-variance-analysis.png" />
</p>
<br />
<br />

I added different versions of the code to work in the online editor, VS Code, or in Power BI. [Auto-size is not supported for composed views](https://vega.github.io/vega-lite/docs/size.html#limitations). Be aware of that if you're importing the composed graphic above (```monthly-variance-analysis-deneb.json``` Deneb template). You have to resize the visual manually by changing the ```width``` and ```height``` properties in the Config tab. 

If you just want a visual that auto-resize without looking at the code, I got you covered. I created separate templates for the following graphics with autosize enabled:

- Actuals vs Forecasts Lipstick Column Chart
<br />
<br />
<p align="center">
  <img src="https://github.com/shadfrigui/vega-lite/blob/0f799574ec0d86ac9a16887fea5685e25caa1ee4/monthly-variance-analysis/actuals-vs-forecasts-lipstick-column-chart.png" />
</p>
<br />
<br />

- Actuals vs Forecasts Bullet-like Chart
<br />
<br />
<p align="center">
  <img src="https://github.com/shadfrigui/vega-lite/blob/0f799574ec0d86ac9a16887fea5685e25caa1ee4/monthly-variance-analysis/actuals-vs-forecasts-bullet-like-chart.png" />
</p>
<br />
<br />

- Variance Column Chart
<br />
<br />
<p align="center">
  <img src="https://github.com/shadfrigui/vega-lite/blob/0f799574ec0d86ac9a16887fea5685e25caa1ee4/monthly-variance-analysis/variance-column-chart.png" />
</p>
<br />
<br />

#### Note
If your data is spanning multiple years, add a **single select** Year slicer to show the correct results for each year.
