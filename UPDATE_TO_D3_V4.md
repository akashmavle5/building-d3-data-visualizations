# Update to D3 Version 4

The latest version of D3, version 4, is not backwards compatible with version 3 used in this course. Some of the major changes to the library include breaking its functionality into [smaller modules](https://github.com/d3), and a change from a logical, nested namespace to a flat namespace (eg. `d3.svg.arc` has changed to `d3.arc`).

The GitHub repo for the course project has been updated to version 4 of D3. You can see the changes in the [commit diff report](https://github.com/tutsplus/building-d3-data-visualizations/commit/1bf61ab97bb6f146b0ad5554d81cd427e68df3ad). 


## Per-Lesson Code Changes

These notes explain the changes that have been made to the code seen in each lesson.

#### Lesson 2.2: Load the Data as CSV

---

**0:57** 
D3 v4 now allows modularity. You can choose to only include specific microlibraries of the build, or you can use the entire library as before:  

Load the D3 library as `<script src="https://d3js.org/d3.v4.js"></script>`. *(index.html, line: 26)*

---


#### Lesson 3.1: Placing SVG on the Page

---

**04:20** 
D3 no longer allows you to include multiple `attr()` in an object. Instead use two separate attr:  

`.attr('width', width + margin.left + margin.right)`  
`.attr('height', height + margin.top + margin.bottom)`   
*(timeline.js, line 9-10)*

Adding the d3-selection-multi library will allow you to to set multiple properties like in v3:  
`<script src="https://d3js.org/d3-selection-multi.v0.4.min.js"></script>`

---

#### Lesson 3.3: Scales and Axes

See the [new documenation for `scale`](https://github.com/d3/d3/blob/master/API.md#scales-d3-scale)

---

**0:45**
`d3.scale.linear` is now `d3.scaleLinear`

---

**1:30** 
`d3.scale.ordinal` is now `d3.scaleOrdinal` or can be `d3.scaleBand`

---

**2:54** 
Instead of `d3.scale.ordinal`, use `d3.scaleBand`. *(timeline.js, line 42)*

---

**3:40** 
Padding should now be declared separately.  

Use `.padding(.05)`. *(timeline.js, line 44-45)*

---

**4:05** 
`d3.svg.axis` has had a major overhaul. Now instead of using `d3.svg.axis`, you can specify `d3.axisBottom()`, `d3.axisTop()`, `d3.axisLeft()`, or `d3.axisRight()`. See the [D3 Axis Documentation for more details(https://github.com/d3/d3/blob/master/API.md#axes-d3-axis).  

Styles are now included with axes. For this design we have to manually remove the axis stroke.  

```
.y-axis path, .x-axis path {
	stroke: none;
}
```
*(index.html, line: 15-17)*

Ticks have changed. In order to remove the ticks added by v4, we manually add:  

```
.tickSize(0)
.tickPadding(0)
```  
*(timeline.js, line: 47-50)*

---

**6:07** 
`d3.scale.linear()` is now `d3.scaleLinear()`

---

**6:37** 
`d3.svg.axis` is now `d3.axisLeft(y)`  

As above with the bottom axis we add tick styling in V4:  

```
.tickSize(0)
.tickPadding(10)
```  
*(timeline.js, line: 58-60)*

---

**9:20** 
Time formatting has changed.  See the [D3 Time Formats Documentation](https://github.com/d3/d3/blob/master/API.md#time-formats-d3-time-format) for more details.  

Use `d3.timeFormat()`. *(timeline.js, line: 50)*

---

#### Lesson 3.4: Visualizing Data

---

**2:00** 
`attr` can no longer be listed as an object.

```
.attr('x', function(d) {return x(d.transDate)})  
.attr('y', function(d) {return y(Math.max(0, d.amount))})  
.attr('width', x.bandwidth())  
.attr('height', function(d) {return Math.abs(y(d.amount) - y(0))})
```  
*(timeline.js, line: 82-85)*

---

**3:30** 
`x.rangeBand()` is now `x.bandWidth()`.	*(timeline.js, line: 84)*

---

**5:34**
`attr` can no longer be listed as an object.

```
.attr('dy', '.3em')  
.attr('dx', '-1em')
```  
*(timeline.js, line: 70-71)*

---

#### Lesson 3.5: Finishing Touches

---

**2:12** 
`d3.time.format` is now `d3.timeFormat`. *(timeline.js, line: 88)*

---

#### Lesson 4.3: Arcs

**0:40** 
`d3.svg.arc()` is now `d3.arc()`. *(pie.js, line 38)*

---

**1:30** 
`d3.svg.pie()` is now `d3.pie()`. *(pie.js, line: 42)*

---

**2:12**
See the new [Pie Layout Documentation](https://github.com/d3/d3/blob/master/API.md#pies)

---

**3:53** 
`d3.scale.category20()` is now `d3.scaleOrdinal(d3.schemeCategory20)`. *(pie.js, line: 52)*

---

**4:00** 
See the new [Ordinal Scales Documentation](https://github.com/d3/d3/blob/master/API.md#ordinal-scales)

---

#### Lesson 4.5: Finishing Touches

---

**2:49**
See the new `d3.format()` [Number Formats Documentation](https://github.com/d3/d3/blob/master/API.md#number-formats-d3-format).

---

**3:25** 
Use `',d'` instead of `',f'`. *(pie.js, line: 98)*	

---

**Note:**
Many bl.ocks.org examples have not been updated. Before using any bl.ocks.org code, check the script url. V4 will include d3.v4 in the path to d3.

## Further Reading:

[https://github.com/d3/d3/blob/master/CHANGES.md](https://github.com/d3/d3/blob/master/CHANGES.md)  
[https://iros.github.io/d3-v4-whats-new/](https://iros.github.io/d3-v4-whats-new/)




