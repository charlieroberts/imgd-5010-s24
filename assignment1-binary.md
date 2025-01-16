# Assignment 1 - Build your own binary (byob)

The goals of this assignment are to make you comfortable with binary numbers / how computers use data,
think about designing programming interfaces, and learn to document your coding projects. The deliverables are as follows:

1. A small, binary, programming interface that enables programmers to accomplish some (small, constrained) drawing task; 
this task should also be able to be executed by hand (with a pencil/pen etc.) This interface is *speculative/imaginary*, 
you will not need to actually implement something that interprets it. As an extremely tiny example, consider the following interface which 
draws a choice of four shapes to four corners:
```
Each command consists of two two-bit words. The first determines the corner,
the second determines the shape.

00 - Upper left
01 - Upper Right
10 - Bottom Right
11 - Bottom Left

00 - Square
01 - Triangle
10 - Circle
11 - Star

A program to draw a square in the upper-left corner and a star in the bottom right corner would be:

00 00 10 11
```
Your example should be more complex than this, but I would limit your word size to four bits (16 possible values) unless you really really want more commands. 
Make sure you write a few example programs for yourself to confirm that your interface "works" the way you think it would.

2. Create a Github repo and a README.markdown file that documents your programming interface. Experiment with the different features that Markdown offers. Try to make the documentation clear but approachable.
   
3. Reach out another member of your class. Ask them to do the following:
- Provide them with a (relatively simple) challenge to realize using your language. You could give them a written description of what to draw, a rendering of the drawing or both.
- Ask them to make something creative with your interface and to draw the output they would expect to see.
- Ask them for their feedback on your interface. Was your documentation clear? What would they change about your interface or add? How difficult was it for them to complete your challenge?
- Complete A-C for their language
- Create a file called `feedback.md` containing the feedback you received and the program your test user created. Upload this and a screenshot of the image your test user drew to your GitHub repo.

4. Place a link to your GitHub repo in the assignment on Canvas. 
