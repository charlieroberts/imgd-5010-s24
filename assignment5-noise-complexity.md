# Noise and Complexity
For this assignment we will experiment with both noise and complexity. The learning goals are:

- Explore ways to organize our code via objects, properties, and methods
- Explore the controlled use of randomness and noise
- Continue getting comfortable with arrays and loops

The requirements for the assignments are as follows:

- Create and control at least 100 "agents"
- Use randomness to influence agent properties -or- use noise to do the same
- Add some type of mouse-based interaction to your sketch, influencing the agents

Aesthetically, we want to think about how randomness can create new, unexpected territories for our
sketches, but also think about using it in a way that it can be *guided* towards interesting results.
That is, you should try to create a coherent piece, not just something that's entirely random.

Create a repo containing your p5 code. In a README file for the repo, briefly state what you were trying to
accomplish and how you think you did / didn't succeed. Include a link to a version of your project running
in editor.p5js.org.

Starter code:  
```js
let agents = []
let count  = 100 

function setup() {
  createCanvas(400, 400)
  
  for( let i = 0; i < count; i++ ) {
    let agent = {
      x: random() * width,
      y: random() * height,
      
      draw() {
        point( agent.x, agent.y )
      }
    }
    agents.push( agent )
  }
  
  strokeWeight( 5 )
  stroke( 'white' )
}

function draw() {
  background( 0 )
  agents.forEach( a => a.draw() )
}
```
