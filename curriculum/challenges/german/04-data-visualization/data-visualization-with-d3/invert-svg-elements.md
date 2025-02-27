---
id: 587d7fa9367417b2b2512bd0
title: Invert SVG Elements
challengeType: 6
forumTopicId: 301488
dashedName: invert-svg-elements
---

# --description--

Vielleicht ist dir aufgefallen, dass das Balkendiagramm auf dem Kopf steht, oder umgedreht ist. This is because of how SVG uses (x, y) coordinates.

In SVG befindet sich der Ursprungspunkt für die Koordinaten in der oberen linken Ecke. An `x` coordinate of 0 places a shape on the left edge of the SVG area. A `y` coordinate of 0 places a shape on the top edge of the SVG area. Higher `x` values push the rectangle to the right. Higher `y` values push the rectangle down.

To make the bars right-side-up, you need to change the way the `y` coordinate is calculated. Es muss sowohl die Höhe des Balkens als auch die Gesamthöhe des SVG-Bereichs berücksichtigt werden.

Die Höhe des SVG-Bereichs ist 100. If you have a data point of 0 in the set, you would want the bar to start at the bottom of the SVG area (not the top). To do this, the `y` coordinate needs a value of 100. If the data point value were 1, you would start with a `y` coordinate of 100 to set the bar at the bottom. Then you need to account for the height of the bar of 1, so the final `y` coordinate would be 99.

The `y` coordinate that is `y = heightOfSVG - heightOfBar` would place the bars right-side-up.

# --instructions--

Change the callback function for the `y` attribute to set the bars right-side-up. Beachte, dass die `height` des Balkens dreimal so hoch ist wie der Datenwert `d`.

**Note:** In general, the relationship is `y = h - m * d`, where `m` is the constant that scales the data points.

# --hints--

The first `rect` should have a `y` value of `64`.

```js
assert($('rect').eq(0).attr('y') == h - dataset[0] * 3);
```

The second `rect` should have a `y` value of `7`.

```js
assert($('rect').eq(1).attr('y') == h - dataset[1] * 3);
```

The third `rect` should have a `y` value of `34`.

```js
assert($('rect').eq(2).attr('y') == h - dataset[2] * 3);
```

The fourth `rect` should have a `y` value of `49`.

```js
assert($('rect').eq(3).attr('y') == h - dataset[3] * 3);
```

The fifth `rect` should have a `y` value of `25`.

```js
assert($('rect').eq(4).attr('y') == h - dataset[4] * 3);
```

The sixth `rect` should have a `y` value of `46`.

```js
assert($('rect').eq(5).attr('y') == h - dataset[5] * 3);
```

The seventh `rect` should have a `y` value of `13`.

```js
assert($('rect').eq(6).attr('y') == h - dataset[6] * 3);
```

The eighth `rect` should have a `y` value of `58`.

```js
assert($('rect').eq(7).attr('y') == h - dataset[7] * 3);
```

The ninth `rect` should have a `y` value of `73`.

```js
assert($('rect').eq(8).attr('y') == h - dataset[8] * 3);
```

# --seed--

## --seed-contents--

```html
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    const w = 500;
    const h = 100;

    const svg = d3.select("body")
                  .append("svg")
                  .attr("width", w)
                  .attr("height", h);

    svg.selectAll("rect")
       .data(dataset)
       .enter()
       .append("rect")
       .attr("x", (d, i) => i * 30)
       .attr("y", (d, i) => {
         // Add your code below this line



         // Add your code above this line
       })
       .attr("width", 25)
       .attr("height", (d, i) => 3 * d);
  </script>
</body>
```

# --solutions--

```html
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    const w = 500;
    const h = 100;

    const svg = d3.select("body")
                  .append("svg")
                  .attr("width", w)
                  .attr("height", h);

    svg.selectAll("rect")
       .data(dataset)
       .enter()
       .append("rect")
       .attr("x", (d, i) => i * 30)
       .attr("y", (d, i) => h - 3 * d)
       .attr("width", 25)
       .attr("height", (d, i) => 3 * d);
  </script>
</body>
```
