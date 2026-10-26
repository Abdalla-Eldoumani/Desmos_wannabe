# Graphing Calculator

A small browser graphing calculator, a student project from 2023. Type one or more expressions in `x`, click Plot, and each one is drawn as a line on a pannable, zoomable graph.

![Screenshot of the graphing calculator](image.png)

## How it works

`script.js` samples 10,000 evenly spaced x values from -1000 to 1000 with numeric.js, evaluates each expression at every point with math.js, and plots the results with Plotly. Each expression gets its own colour and legend entry, and hovering shows the point's coordinates.

Before evaluating, it inserts a `*` between a digit and a following letter, so `2x` becomes `2 * x` and `3sin(x)` becomes `3 * sin(x)`. Anything math.js understands works otherwise, for example `x^2 - 4`, `sin(x) / x`, or `abs(x)`. An expression that fails to parse shows an alert with its number.

## Run it

Open `index.html` in a browser. There is no build step. Plotly, numeric.js and math.js load from CDNs, so you need an internet connection.

## Usage

- Enter an expression in the input box. Click **Add Equation** for more boxes.
- Click **Plot** to draw every non-empty expression.
- Drag to pan and scroll to zoom. The Plotly toolbar has reset and download options.

To change the plotted range or the number of sample points, edit the `numeric.linspace(-1000, 1000, 10000)` call at the top of `script.js`.

## Limitations

- Only explicit functions of `x` are supported. Implicit equations such as `x^2 + y^2 = 1` and inequalities are not.
- The range is fixed at -1000 to 1000, so the default view is very zoomed out for most functions.
- The digit-letter rewrite also changes scientific notation, so `1e3` is read as `1 * e3` and fails.
