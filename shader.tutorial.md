# Diving into some basic shader programming using The Force:

Shawn Lawson's [The Force](https://shawnlawson.github.io/The_Force/) is a fantastic environment for live coding GLSL shaders. We'll use it to do some initial GLSL experiments creating waveforms.

Our first shader in GLSL:
```c
// we have to define a main function (like C)
void main () {
  // gl_FragColor determines our final color output
  // it is a list of four numbers (vec4) with r,g,b,a values

  gl_FragColor = vec4( 1., 0., 0., 1. );
}
```

It is important to note that most numbers are floating point and **must have a decimal point to indicate this**. It is really easy to forget this, especially coming from JavaScript, so be careful!

## Creating an oscillator
The Force comes pre-programmed with special **uniforms** (a uniform is a value transferred from the CPU to the GPU). One such value is `time`. We can use this to make a simple sine wave:

```c
void main () {
  float frequency = 4.;
  float color = sin( time * frequency );
  gl_FragColor = vec4( color,color,color, 1. );
}
```

However, you’ll notice that this spends a half of each cycle as black, because the `sin()` function returns values between -1 – 1. We can provide a bias and a scalar to get this to a range of 0–1:

```c
void main () {
  float frequency = 4., bias = .5, gain = .5;
  float color = bias + sin( time * frequency ) * gain;
  gl_FragColor = vec4( color,color,color, 1. );
}
```

## Varying our oscillator over space
The Force comes with a function `uv()` that returns the `x` and `y` coordinates of the current pixel being calculated. We can use this to make a classic video oscillator on our screen.

```c
void main () {
  vec2 p = uv();
  float frequency = 10.;
  float color = sin( p.x * frequency + time );
  gl_FragColor = vec4( color,0.,0., 1. );
}
```

… and now’s where things start to get fun. We can easily use the x and y values to create all sorts of interesting variations on this. Try this one:

```c
void main () {
  vec2 p = uv();
  float frequency = 10.;
  float color = sin( p.x / p.y * frequency  + time );
  gl_FragColor = vec4( color,0.,0., 1. );
}
```

What happens when you multiply `p.x` by `p.y` instead of dividing it? What happens when you multiply the entire output of the `sin()` function by `p.y`? All sort of fun variations to play with.

## Classic live shader programming videos:

- Hexler - [codelife - glsl live-coding editor test #5 on Vimeo](https://vimeo.com/51993089)
- Shawn Lawson - [RISC Chip - Mint: Kindohm. Visuals: Obi Wan Codenobi on Vimeo](https://vimeo.com/192920872)

## Let’s make a Hexler-style sine wave and use an FFT
```c
void main() {
  vec2 p = uvN();
  float color = 0.; 
  float frequency = 2.;
  float gain = 1.;
  float thickness = .05;

  p.x += sin( p.y * frequency + time * 4.) * gain; 
  color = abs( thickness / p.x );

  gl_FragColor = vec4( color );
}
```

OK, that’s fun, but the only thing better than a sine wave is twenty sine waves:

```c
void main() {
  vec2 p = uv();
  float color = 0.; 
  float frequency = 2.;
  float gain = 1.;
  float thickness = .025;

  for( float i = 0.; i < 10.; i++ ) { 
    p.x += sin( p.y + time * i) * gain; 
    color += abs( thickness / p.x );
  }

  gl_FragColor = vec4( color );
}
```

### Adding the FFT
In The Force, we can get access to the data from our laptop microphones by clicking on the microphone button at the bottom of the screen. Once you’ve granted Firefox access to use the microphone, the FFT data will then be available in a four-item uniform named `bands`, where `bands[0]` is the low-frequency content and `bands[3]` is the high frequency content. Try setting the value of `gain` in the above script to use one of these bands and have fun watching the results… and then try messing around with the formula in other ways, dividing instead of of multiplying, use fewer or more iterations of the for loop etc.
