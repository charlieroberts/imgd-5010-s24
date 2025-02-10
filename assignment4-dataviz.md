# Data Visualization

This assignment will explore data visualization as a creative medium. The goals of the assignment are:

1. Get comfortable examining / using data structures (JSON)
2. Get experience with arrays and loops
3. Learn how to load external data
4. Think about data as an abstraction for creative inspiration

Find external data to load in to p5.js. This could be a local file that you upload to the p5.js editor, or you
could [find an API to load data from](https://github.com/jdorfman/awesome-json-datasets). Below is some starter code to
experiment with:

```js
function setup() {
  background(0)
  createCanvas(400, 400);
  // load json data and store in variable test
  test = loadJSON('https://api.exchangerate-api.com/v4/latest/USD')
}

function draw() {
  background(220)

  // convert dictionary to flat array of values
  const rates = Object.values( test.rates )

  // loop through rates and visualize
  for( let i = 0; i < rates.length/10; i++ ) {
    fill(0)
    text( rates[i], i*20, i*20 )
    fill(255,0,0,64)
    circle( i * 20, i * 20, rates[i] )
  }

  // only draw once
  noLoop()
}
```

Submit a repo to the Canvas assignment with the following:
1. Your code in a .js file
2. A README.md file containing a link to your code running at https://editor.p5js.org and a brief (<300 words) description of what you created
and what your goals were.

This assignment is due Thursday Feb. 13 by the start of class.
