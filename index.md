---
title       : rCharts-Tutorial
subtitle    : 
author      : Vivek Patil
job         : Associate Professor of Marketing
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, interactive]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

## rCharts

* Provides the ability, from within R, to create, customize and publish interactive JavaScript (JS) visualizations
* JS is a computer programming language that can create interactivity using web browsers
* There are many pre-written JS libraries that make the process of creating visualizations easier. 
* rCharts provides wrapper functions around few, but among the best, of these JS libraries to let an R user create interactive JS visualizations with little knowledge of JS. 

---

## JS libraries currently supported (as of 10/2014)

|   |   |
|---|---|
| [datatables](http://www.datatables.net/)  | Interactive tables  |
| [dimple](http://dimplejs.org/)  | d3-based - plenty of options  |
| [highcharts](http://www.highcharts.com/)  |Free only for non-commercial purposes, plenty of options   |
| [morris](http://morrisjs.github.io/morris.js/)  | currently - line, bar, area and donut charts  |
| [nvd3](http://nvd3.org/)  | d3-based - plenty of options   |
| [polychart](https://www.polychart.com/js/)  | Free for non-commercial purposes only  |
| [rickshaw](http://code.shutterstock.com/rickshaw/)  |d3-based, time-series specialty but many others |
| [timeline](http://timeline.knightlab.com/)  | Interactive timelines  |
| [uvcharts](http://imaginea.github.io/uvCharts/)  | d3-based   |
| [xcharts](http://tenxer.github.io/xcharts/)  |  Examples of line and bar charts and custom modifications of these  |

* datamaps, leaflet, and crosslet are 3 others that have been wrapped up in another package called rMaps (for a different day)

---

## Challenge in learning

* Different JS libraries developed independently - consistency in calls from within rCharts can at times be a challenge
* Customization to specific needs may require writing JS code

### Learning approach

* Follow examples, questions, and issues presented in different venues
* Stick to rCharts interface to few JS libraries which provide many choices of charts and become very familiar with them. Don't forget that few have restrictions for commercial use.

---

## Few Resources

* [rCharts' website](http://rcharts.io/) and its [gallery of submissions from different people](http://rcharts.io/gallery/).
* [rCharts on GitHub and the issues posted there](https://github.com/ramnathv/rCharts) and on [stackoverflow](http://stackoverflow.com/search?q=rCharts)
* [A work-in-progress documentation](http://timelyportfolio.github.io/docs/_build/html/)
* [rCharts-related posts from different bloggers via R-bloggers](http://www.r-bloggers.com/?s=rCharts)


|Code examples for different libraries   |   |
|---|---|
| [datatables](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/datatables/examples.R)  | [polychart](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/polycharts/examples.R)    |
| [dimple](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/dimple/examples.R)  | [rickshaw](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/rickshaw/examples.R)  |
| [highcharts](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/highcharts/examples.R)  | [timeline](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/timeline/examples.R)  |
| [morris](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/morris/examples.R)  | [uvcharts](http://imaginea.github.io/uvCharts/)  |
| [nvd3](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/nvd3/examples.R)  | [xcharts](https://github.com/ramnathv/rCharts/blob/master/inst/libraries/xcharts/examples.R)   |

---

## Datatable




```r
dt <- dTable(
  iris,
  sPaginationType= "full_numbers"
)
dt$save('datatable.html',cdn=TRUE)
```
<iframe src="datatable.html"></iframe>

---
## Dimple - Verticle stacked & Grouped Bar Chart (the documentation and examples are most extensive)


```r
data <- read.delim(
  "http://pmsi-alignalytics.github.io/dimple/data/example_data.tsv"
)
colnames(data) <- gsub("[.]","",colnames(data))
d1 <- dPlot(
  x = c("PriceTier","Channel"),
  y = "UnitSales",
  groups = "Owner",
  data = data,
  type = "bar"
)
d1$legend(
  x = 200,
  y = 10,
  width = 400,
  height = 20,
  horizontalAlign = "right"
)
d1$save('dimple.html',cdn=TRUE)
```

---

## Dimple: Verticle stacked & Grouped Bar Chart (the documentation and examples are most extensive)

<iframe src="dimple.html"></iframe>

---

## Highchart: Bubble Chart with Zoom and Export (plenty of other cool ones)


```r
h1 <- hPlot(Pulse ~ Height, data = MASS::survey, type = "bubble", title = "Zoom demo", subtitle = "bubble chart", size = "Age", group = "Exer")
h1$chart(zoomType = "xy")
h1$exporting(enabled = T)
h1$show("inline")
```


<div id = 'chart1ee420044bf' class = 'rChart highcharts'></div>
<script type='text/javascript'>
    (function($){
        $(function () {
            var chart = new Highcharts.Chart({
 "dom": "chart1ee420044bf",
"width":            800,
"height":            400,
"credits": {
 "href": null,
"text": null 
},
"exporting": {
 "enabled": true 
},
"title": {
 "text": "Zoom demo" 
},
"yAxis": [
 {
 "title": {
 "text": "Pulse" 
} 
} 
],
"series": [
 {
 "data": [
 [
         154.94,
71,
        17.167 
],
[
          156.2,
80,
          28.5 
],
[
            157,
74,
        35.833 
],
[
            157,
74,
            18 
],
[
            157,
89,
        19.333 
],
[
         157.48,
68,
         17.75 
],
[
         160.02,
80,
          18.5 
],
[
         162.56,
60,
        17.417 
],
[
            164,
64,
        18.583 
],
[
            164,
64,
        20.167 
],
[
            164,
84,
        23.083 
],
[
            165,
48,
        18.667 
],
[
            165,
80,
        18.167 
],
[
            165,
92,
            20 
],
[
          165.1,
87,
        17.083 
],
[
          166.4,
72,
         39.75 
],
[
          166.5,
60,
         23.25 
],
[
            167,
70,
        20.333 
],
[
         167.64,
40,
        17.417 
],
[
         167.64,
70,
        17.333 
],
[
         167.64,
72,
        17.333 
],
[
         167.64,
90,
        17.167 
],
[
            168,
83,
        17.083 
],
[
          168.5,
85,
         17.75 
],
[
          169.2,
60,
        29.083 
],
[
            170,
64,
        17.583 
],
[
            170,
68,
        20.667 
],
[
            170,
70,
        23.833 
],
[
            170,
75,
         18.75 
],
[
            170,
104,
         17.25 
],
[
         170.18,
75,
        21.167 
],
[
         170.18,
80,
            17 
],
[
            172,
68,
        19.167 
],
[
            172,
68,
        23.417 
],
[
            172,
73,
          21.5 
],
[
            172,
92,
          17.5 
],
[
         172.72,
65,
         17.25 
],
[
         172.72,
68,
        17.667 
],
[
         172.72,
69,
        70.417 
],
[
         172.72,
76,
        36.583 
],
[
            173,
62,
        20.333 
],
[
            173,
76,
        23.583 
],
[
            174,
48,
        21.333 
],
[
            175,
72,
        20.167 
],
[
            175,
76,
        24.167 
],
[
         175.26,
62,
        18.083 
],
[
         175.26,
66,
            21 
],
[
         175.26,
68,
        19.083 
],
[
          176.5,
76,
        20.167 
],
[
            177,
76,
         18.25 
],
[
            177,
78,
        17.917 
],
[
          177.8,
62,
        17.667 
],
[
            178,
70,
          17.5 
],
[
          178.5,
66,
        18.083 
],
[
            179,
56,
        17.417 
],
[
            179,
60,
        21.583 
],
[
            179,
65,
        22.833 
],
[
            180,
59,
        17.417 
],
[
            180,
64,
        18.583 
],
[
            180,
78,
          17.5 
],
[
            180,
84,
        18.917 
],
[
         180.34,
64,
        17.833 
],
[
         180.34,
70,
        17.417 
],
[
         180.34,
72,
        18.167 
],
[
         180.34,
72,
        17.333 
],
[
            182,
65,
            20 
],
[
          182.5,
72,
        17.917 
],
[
         182.88,
72,
        19.333 
],
[
         182.88,
83,
        18.833 
],
[
            184,
100,
        20.083 
],
[
            185,
60,
        17.917 
],
[
            185,
68,
        17.417 
],
[
            185,
71,
        19.333 
],
[
            185,
88,
        19.333 
],
[
         185.42,
60,
        32.667 
],
[
            187,
66,
        20.333 
],
[
            187,
84,
        17.917 
],
[
         187.96,
64,
            23 
],
[
         187.96,
86,
            20 
],
[
            188,
75,
        18.917 
],
[
            190,
66,
            18 
],
[
            190,
68,
          17.5 
],
[
            190,
68,
        19.417 
],
[
          190.5,
72,
        17.917 
],
[
            195,
76,
          25.5 
],
[
            196,
63,
        20.083 
],
[
            200,
55,
          18.5 
] 
],
"name": "Freq",
"type": "bubble",
"marker": {
 "radius":              3 
} 
},
{
 "data": [
 [
         157.48,
70,
        17.167 
],
[
            158,
70,
          20.5 
],
[
            160,
86,
        20.167 
],
[
            165,
50,
         30.75 
],
[
            165,
65,
          18.5 
],
[
            165,
97,
          19.5 
],
[
            167,
68,
        18.667 
],
[
            167,
80,
        18.417 
],
[
            170,
60,
         17.75 
],
[
            170,
96,
        19.417 
],
[
            176,
68,
        18.917 
],
[
          177.8,
104,
        17.583 
],
[
         180.34,
68,
        43.833 
],
[
          190.5,
80,
        18.167 
] 
],
"name": "None",
"type": "bubble",
"marker": {
 "radius":              3 
} 
},
{
 "data": [
 [
            152,
90,
        18.333 
],
[
          152.4,
92,
          23.5 
],
[
          153.5,
76,
        17.417 
],
[
         154.94,
72,
        17.083 
],
[
            155,
66,
          17.5 
],
[
            159,
70,
        22.917 
],
[
            160,
74,
        17.167 
],
[
            160,
84,
        18.583 
],
[
            160,
88,
        16.917 
],
[
         160.02,
65,
         32.75 
],
[
         160.02,
72,
         17.25 
],
[
          162.5,
79,
         17.25 
],
[
         162.56,
70,
            18 
],
[
         162.56,
70,
        17.167 
],
[
         162.56,
88,
        18.167 
],
[
            163,
79,
        24.667 
],
[
            163,
80,
        17.667 
],
[
            163,
83,
         17.25 
],
[
            164,
80,
          17.5 
],
[
            165,
35,
        23.667 
],
[
            165,
65,
        20.417 
],
[
            165,
70,
        19.667 
],
[
            165,
76,
        23.583 
],
[
            165,
76,
          26.5 
],
[
            165,
88,
         17.75 
],
[
          165.1,
68,
        17.083 
],
[
          165.1,
85,
        17.667 
],
[
            167,
61,
         19.25 
],
[
            167,
76,
         17.25 
],
[
            167,
79,
         19.25 
],
[
            167,
90,
        22.333 
],
[
         167.64,
74,
         44.25 
],
[
            168,
60,
        18.417 
],
[
            168,
72,
        21.167 
],
[
            168,
81,
          18.5 
],
[
          168.9,
68,
        17.083 
],
[
            169,
80,
        18.167 
],
[
            170,
70,
        18.167 
],
[
            170,
80,
         18.25 
],
[
            170,
80,
        19.167 
],
[
         170.18,
78,
        18.333 
],
[
         170.18,
80,
        18.417 
],
[
            171,
68,
        17.667 
],
[
            171,
100,
        18.917 
],
[
            172,
60,
        28.583 
],
[
         172.72,
64,
            21 
],
[
         172.72,
90,
          17.5 
],
[
            173,
92,
         18.25 
],
[
            175,
72,
            19 
],
[
            175,
84,
          17.5 
],
[
            175,
90,
         18.75 
],
[
         175.26,
85,
        18.417 
],
[
          176.5,
80,
          17.5 
],
[
            178,
60,
         18.75 
],
[
          179.1,
80,
        18.667 
],
[
          179.1,
92,
        18.917 
],
[
            180,
60,
        27.333 
],
[
            180,
70,
        17.167 
],
[
            180,
96,
            19 
],
[
         180.34,
67,
         17.75 
],
[
         182.88,
74,
        18.333 
],
[
         182.88,
80,
        18.667 
],
[
            183,
75,
        19.667 
],
[
            183,
90,
        17.167 
],
[
            184,
62,
         18.25 
],
[
            185,
75,
            19 
],
[
            185,
80,
          35.5 
],
[
            189,
90,
        19.167 
],
[
          191.8,
72,
          17.5 
],
[
         193.04,
83,
        18.917 
] 
],
"name": "Some",
"type": "bubble",
"marker": {
 "radius":              3 
} 
} 
],
"xAxis": [
 {
 "title": {
 "text": "Height" 
} 
} 
],
"subtitle": {
 "text": "bubble chart" 
},
"chart": {
 "zoomType": "xy",
"renderTo": "chart1ee420044bf" 
},
"id": "chart1ee420044bf" 
});
        });
    })(jQuery);
</script>

---
# Morris - line chart


```r
data(economics, package = 'ggplot2')
dat = transform(economics, date = as.character(date))
m1 <- mPlot(x = "date", y = list("psavert", "uempmed"), data = dat, type = 'Line',
            pointSize = 0, lineWidth = 1)
m1$set(xLabelFormat = "#! function (x) { 
  return x.toString(); } 
!#")
m1$save("morris.html",cdn=TRUE)
```
<iframe src="morris.html"></iframe>

---
## nvd3: Grouped/Stacked Bar Chart (plenty of cool examples - check out the line with focus)


```r
hair_eye = as.data.frame(HairEyeColor)
n1 <- nPlot(Freq ~ Hair, group = 'Eye', data = subset(hair_eye, Sex == "Female"), type = 'multiBarChart')
n1$chart(color = c('brown', 'blue', '#594c26', 'green'))
n1$save('nvd3.html',cdn=TRUE)
```
<iframe src="nvd3.html"></iframe>

--- 
## polycharts: facetted bar plot (also check out their heatmap)


```r
names(iris) = gsub("\\.", "", names(iris))
p1 <- rPlot(SepalLength ~ SepalWidth | Species, data = iris, color = 'Species', type = 'point')
p1$save("polychart.html",cdn=TRUE)
```
<iframe src="polychart.html"></iframe>

---
## Rickshaw: Area chart


```r
uspexp <- reshape2::melt(USPersonalExpenditure)
names(uspexp) <- c('category', 'year', 'expenditure')
to_jsdate <- function(date_){
  val = as.POSIXct(as.Date(date_), origin="1970-01-01")
  as.numeric(val)
}
uspexp <- transform(uspexp, year = to_jsdate(as.Date(paste(year, '01', '01', sep = '-'))))
r1 <- Rickshaw$new()
r1$layer(expenditure ~ year, group = 'category', data = uspexp, type = 'area')
r1$yAxis(orientation = 'left')
r1$xAxis(type = 'Time')
r1$set(width = 700, height = 400)
r1$save("rickshaw.html",cdn=TRUE)
```

---
## Rickshaw: Area chart

<iframe src="rickshaw.html"></iframe>

---

## UV Charts


```r
u1=uPlot(x = 'Sex', y = 'Freq', data = as.data.frame(HairEyeColor), group = 'Hair', type = 'Bar')
u1$save("uv.html",cdn=TRUE)
```
<iframe src="uv.html"></iframe>

---

## Displaying/Distributing them

* `chartname$save('chartname.html')` and then use iframe 
* `chartname$publish('chartname.html')` # need a GitHub account

(See [rCharts Issue# 373 for other options](https://github.com/ramnathv/rCharts/issues/373))

---

## Few Resources, again

* [rCharts' website](http://rcharts.io/) and its [gallery of submissions from different people](http://rcharts.io/gallery/).
* [rCharts on GitHub and the issues posted there](https://github.com/ramnathv/rCharts) and on [stackoverflow](http://stackoverflow.com/search?q=rCharts)
* [A work-in-progress documentation](http://timelyportfolio.github.io/docs/_build/html/)
* [rCharts-related posts from different bloggers via R-bloggers](http://www.r-bloggers.com/?s=rCharts)

* [One of my posts on different charts rCharts provides for different questions](http://patilv.com/Replication-of-few-graphs-charts-in-base-R-ggplot2-and-rCharts-part-3-rCharts/)

Code for this presentation can be found at: [https://github.com/patilv/rCharts-tutorial](https://github.com/patilv/rCharts-tutorial)
