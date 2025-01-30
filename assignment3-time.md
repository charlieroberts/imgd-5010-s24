Due Feb 6th

Art in the early twentieth century took a radical turn from representation to abstraction, from emotion to formal study. While the Bauhaus movement is perhaps best known for this work---from the paintings of Paul Klee to the tapestries of Anni Albers and everything in between---other artists were exploring the use of time and movement in visual composition, in a genre of art often termed *Visual Music*, as music provided the type of control over time, space, and form that these artists were interested in.

For this assignment, you will create a formal piece of visual music, an animation that focuses on developing
and playing with a single graphical element over time. This element could be a rectangle, a circle, a letter,
or any other shape; what's important is that you constrain yourself to it and it alone. The element can be duplicated,
arranged in groups, rotated, scaled etc. Questions to explore:

1. How do you create an animation with an observable structure? One structure might be introduction, development, climax, fade, but another might be to change the composition over time via subtraction rather than (the arguably more traditional) addition.
2. What different ways can you manipulate your element? Will audiences notice subtle changes, or are more dramatic changes required
3. Do you want to enable mouse interaction with your piece? What does the interplay between interaction and time look like in your composition?
4. Do you want a background audio track? It can be difficult to sync sound to music without doing computational analysis of the audio, but it's still a fun challenge.

Here is one possible way to structure time in your composition:

```js
let x = 0
function setup() {
  createCanvas(400,400)
}
function draw() {
  if( frameCount < 300 ) {
	// first five seconds assuming 60 fps
	x += 1
  }else if( frameCount < 600 ) {
    // seconds 5-10
    x += 2 
  }else if( frameCount < 900 ) {
    // seconds 10-15
    x += 5
  }
  background( 255 )
  circle( x, 50, 10 )
}
```
   
Another way is to change the value of variables at specific points. JavaScript has a function for this called `setTimeout`, that lets you call a function at some point in the future (measured in milliseconds):

```js
let x = 0
// call function after (roughly) 10000 milliseconds
setTimeout( function() { x = 100 }, 10000 )
setTimeout( function() { x = 500 }, 20000 )
```

More complex structures for controlling your piece over time are certainly possible, but would require extra programming background... some of which we'll get started on next week! 

## Deliverables:

1. Put your code in a repo, and link to this repo from the Canvas assignment.
2. Include a README.md file in your repo, that explains what formal element you were exploring, what creative inspiration you found, and describes the structure of your composition.
3. We'll use some of class time next week to solicit feedback, so there is no required feedback component this week.
