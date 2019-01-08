# Basics of Processing

## What is Processing?

Processing is a software that offers us a lot of possibilities that we would also find in regular graphic design software \(like Adobe Illustrator\). Both enable us to draw some graphics on a canvas and export it in different ways. But Processing has the power repeat different operations very quickly and use external or random data together in a defined logical way to create things that are not possible in Adobe Illustrator.

The reason behind this difference is the nature of the two: With Adobe Illustrator, we use a general purpose software. It is a mere reflection of the design processes before computers. With Processing, we build a specialized software with the help of programming, incorporating the true power of the digital.

Processing calls the software pieces, that you create, _sketches_. So, when you are writing code in Processing, you are writing a _sketch_.

## It's all code

A fundamental difference between working with traditional design software and tools like Processing is our  output. Traditionally we would move vectors or pixels. For Processing we have to write text. This text is called code. Processing interprets this code to run its operations. You will never have draw a rectangle or bézier curve by hand. It's all described in code.

## Getting Processing

You can find documentation and downloads on the official [website](https://processing.org/) of Processing.

## Is there other software like Processing?

_What_ we do in Processing can be done in any widespread programming language you can probably think of. But _how_ we do it is especially easy and lean in Processing. Processing is free, there is not much need for installations and Processing sketches are only one file, easy to share and uncomplicated. It also offers a lot of things we use as graphic designers, without the need to care about anything.

So Processing is an ideal starting point for generative design (and every other graphical computation), especially for beginners. We do not have to take care of all the other tedious implications that programming normally has.

It is made by designers and artists for designers and artists.

## Why not work in the browser, for example with p5.js?

In recent times you probably felt a hype about web technologies. Web development is advancing on a fast pace and offering almost all the possibilities you have in desktop computing. For Processing, there is a web based co-evolution called [p5.js](https://p5js.org/).

p5.js is a great tool. Nonetheless it implicates all the complexities that you have in web development. If you are interested in training on the latest state of web development, then you should consider using p5.js. If you are more interested in learning the algorithmic part behind Generative Design, I would recommend using Processing.

## A common ground to start

In every class I have taught so far students had a profound knowledge of Adobe Illustrator. I will use it as an analogy to create some references in terminology and work flow. In the first paragraphs, as long as necessary, I will use Illustrator as a comparison to Processing.

## The very basics of Processing

Once you open Processing for the first time, you will not see much. What you see is an empty text editor and a big play button on top. Clicking on that play button will run your software, as soon as you have written some code. Right now not much will happen. We first need to define some basics.

## Setting up your sketch

In Adobe Illustrator, when you want to create a new design document, the first thing that will show up, is a prompt for your basic settings like document size and color space. This is an initial step for setting up your project and is required. You need it only once in the beginning though. When you are drawing in Illustrator, you don't have to think about these settings anymore.

In Processing we have to do something similar too. Processing needs some basic information, for example the size of the canvas it will create, when we run it. We have a way of defining these initial settings, that are needed, exactly once, when we start the sketch.

```java
void setup() {
    // Initial settings of a canvas:
    size(800, 800);
}
```

Woah! There is a lot going on at once. Weird parentheses alarm! Don't worry, at this stage you only have to care about the abstract concept behind this, which I'm trying to explain you with the help of the analogy. The rest, like `void` or these `()`, `{}` and `//` I will explain further down.

We have two important things here. First writing `setup`. When you run your own sketch, Processing will look for a way to set up your sketch. The most important setting that we have to define is the size of the window. By using `size` with two values, Processing will create a window with the width and height values that you have stated in code. So in our example the windows would be a square width an edge length of 800 pixels.

## How does the canvas work?

Using different values in `size` depends on the size of your display. Your screen has a certain resolution and your `size` values have to be smaller.

For example, if you have a display with a resolution of `1920` by `1080`, reasonable values would be `size(1600, 900);`

When you run a sketch with your graphical output will open. This window has a canvas, and it is exactly the size that you specified with `size`. Everything your code draws will be drawn on this canvas.

One important concept is the origin of the canvas. Technically speaking the origin is the point with the values `0, 0`. In Illustrator it it on the top left of you canvas. In Processing it is the top left of the window of your running sketch.

The origin is important because every other positional value is measured in reference to it. If you draw a circle at `0, 0`, it will be exactly in the top left of your canvas. If you increase the x value, the circle would be further to the right. If you increase the y value, the circle would be further to the bottom.

## Drawing on the canvas

In Illustrator, as soon as you have created a document with your custom settings, you will get an empty canvas. Now you are ready to draw your vector graphics.

As you have seen above, in Processing we have to think everything in code. You will not get a canvas on which you can place your elements. Instead our canvas is written text, too. You have to describe what you want to be drawn. The basic structure looks like this:

```java
void setup() {
    // Initial settings of a canvas:
    size(800, 800);
}

void draw() {
    // This will be drawn on the canvas you defined above:
    line(200, 600, 600, 200);
}
```

As you can see we added another one of these constructs to our code. Maybe you can already recognize a pattern. Similar to `setup`, Processing is searching for something called `draw`, that carries the definition of what it should draw for us. In both cases, whatever should be done is defined between these curly brackets `{` and `}`. Why we have to use this I will explain later but this will actually state that the code between either belongs to `setup` or `draw`.

You could copy and paste this code into an empty Processing sketch and you will get a window with a line that goes from bottom left to top right. Why? Because we said so. We used a command called `line` that actually draws a line from one point to another.

## Things we have to do in Processing

As you can see above every line is dedicated to tell Processing one thing at a time how it should behave. We simply call this _commands_ by now.

A lot of these little elements you can see in the examples above are purely cosmetic. For example using a new line for each command or making indentations in certain areas is not necessary for the code to run. We do it because we can read it much better. Code is primarily meant to be read by humans. These elements make it a lot easier for us.

Other elements might disturb you while reading but are necessary for Processing. The semicolon `;` tells Processing where one command ends and another begins. It is necessary for the unambiguity of code.

The different parentheses and brackets you can see above behave the same. Processing is pretty much concerned about you using these correctly. It will complain pretty explicitly if you fail at using them right.

## Graphical elements

As designers, a lot of commands we use in Processing should be very familiar to you. They are quite similar to the primitive shapes you can draw in Illustrator too.

Here is an incomplete list of possibilities to draw something to the screen:

* Lines by using `line`, e.g., `line(100, 200, 400, 500);`
* Circles by using `ellipse`, e.g., `ellipse(400, 400, 200, 200);`
* Rectangles by using `rect`, e.g., `rect(100, 100, 300, 300);`
* Quadrilaterals \(irregular shape with four corners\) by `quad`, e.g., `quad(100, 100, 600, 100, 600, 500, 100, 600);` 
* Triangles by using `triangle`, e.g., `triangle(100, 100, 600, 400, 100, 700);`
* Bézier curves by using `bezier`, e.g., `bezier(100, 100, 600, 100, 600, 600, 100, 600);`

All numbers in the examples above mean something else, depending on the command. What all of them have in common is that they describe spatial relation through pixel values.

For example a `line` is drawn from one point to another. The first two values describe the x and y positions of the first point and the last two values the x and y coordinates of the second point. `quad`, `triangle` and `bezier` behave similarly. These commands connect point.

`ellipse` and `rect` behave different. The first two values again describe the starting point \(x and y position\) of where it should be drawn. The second value pair describes expansion though. In the case of `ellipse` it describes the horizontal and vertical diameter. In the case of `rect` it describes the width and height of the rectangle.

With these few commands we already get incredibly far. Of course they will reach their limits eventually but Processing has a lot more to offer.

## Styling elements

If you tried the commands from above already you will see that Processing will draw mostly shapes with white fill and black outline for you.

Styling in Processing works as easy as in Illustrator. You define a color for the fill and a color and width for the outline. Alternatively you can decide not to use a fill or an outline.

Processing also uses hex values just like any other software, e.g., red would translate into `#FF0000`, gray would translate into `#212121`, and so on.

These are all commands you need to style your shapes:

* Fill color by using `fill`, e.g., `fill(#FF0000);`
* Outline color by using `stroke`, e.g., `stroke(#FF0000);`
* Outline thickness in pixel values by using `strokeWeight`, e.g., `strokeWeight(5);`

If you don't want to show either fill or outline:

* Hiding the fill by using `noFill`, e.g., `noFill();`
* Hiding the outline by using `noStroke`, e.g., `noStroke();`

Further down we will learn how to properly use these commands. Here is an example of how they could be used.

```java
noStroke();
fill(#0000FF);
ellipse(400, 400, 200, 200)
```

The example above would create a blue circle.

Styles always have to be defined before we draw an element.

## Styling the background of the canvas

The style of the canvas is straightforward: You can assign a color to it.

* Fill the color of the canvas by using `background`, e.g., `background(#FAFAFA);`

The `background` command is filling the whole window is with one color. This means that everything that was drawn before will be overdrawn.

## Order of drawing

You probably want to draw more than one element to the screen. In that case you may ask which elements will be drawn on top and which on bottom. In Illustrator this is defined by the concept of layers. An element higher in the layer view will be drawn further to the top.

In Processing it is much simpler. New elements are always drawn on top. Just like on a real canvas. You cannot apply color under the layers that you already have painted.

Code in Processing runs from top to bottom. This means that elements lower in code will be drawn on top.

```java
rect(100, 200, 400, 300);
ellipse(400, 300, 200, 200);
```

In the example above the circle will be drawn on top of the rectangle because it is lower in code.

```java
rect(100, 200, 400, 300);
ellipse(400, 300, 200, 200);
background(#FFFFFF);
```

In the example above you would only see a white window because the background fill is drawn after the rectangle and the circle and therefore on top.

```java
background(#FFFFFF);
rect(100, 200, 400, 300);
ellipse(400, 300, 200, 200);
```

This would be the right way if you want to see a rectangle and a circle in a white window.

## Styling multiple elements

Determined through the order in which Processing goes through our code \(from top to bottom\) we are able to style multiple elements.

The basic principle is that we apply styles _before_ we draw elements. Just like in Illustrator where you could pick colors before you draw an element.

If you want to apply a style to multiple elements, just write the style before the elements.

```java
noStroke();
fill(#FF0000);
rect(200, 200, 400, 400);

ellipse(400, 400, 700, 700);
```

This will draw a red rectangle and ellipse without outlines.

If you want to style elements differently, put the commands before each element.

```java
noStroke();
fill(#FF0000);
rect(200, 200, 400, 400);

stroke(#FF0000);
noFill();
ellipse(400, 400, 700, 700);
```

This will draw a white circle without fill on top of a red square without outline.

## Comments

Processing tries to interpret every single line of code, one by one. Unless you don't want it do that.

We can write text that is only readable by us but skipped by Processing. It is called _comments_.

`// This would be a simple comment and will be ignored by Processing.`

As you can see in the example above, Processing needs a special indicator so it knows that a line is a comment. We can use `//`.

Comments are a good way to document your code for other people or yourself. We tend to forget what we wanted to effect with our code after a couple of days. So we might help our future selfs just by using comments here and there.

You can use comments also for disabling code.

```java
// rect(200, 200, 400, 400);
ellipse(400, 400, 700, 700);
```

In the example above only the ellipse will be drawn because the rectangle is _commented out_.

There is another way to write comments which affects multiple lines.

```java
/*
    Hello
    This is a comment over multiple lines
*/
rect(200, 600, 600, 200);
```

The example above shows how we can use `/*` to open and `*/` to close a comment over multiple lines.

## Errors

Processing is alway quite explicit about something going wrong. There is no exception. If something does not work as expected, Processing will quit execution without mercy. This can be frustrating at times, but generally is a good thing.

Especially in the beginning of learning to code you will make some easy to fix mistakes. Here is a list of common errors:

* You forgot the `;` at the end of a line
* You closed one `)` or `}` to much or too few
* You misspelled a command like `setup`
* You didn't put things where Processing expected them, e.g., a command outside of `setup` or `draw`

These mistakes happen to everyone. You don't have to panic when Processing shows you a bright red error notification. Just try to find the error. Processing is mostly really good a giving you a hint where you have to search.

## Examples to illustrate the previously learned

Below you find working examples of the concepts we discussed above. You can simply copy and paste them into a blank Processing sketch.

```java
// Three circles in a row

void setup() {
  size(1200, 800);
}

void draw() {
  background(#212B36);

  noFill();
  stroke(#BBE5B3);
  strokeWeight(3);
  ellipse(500, 400, 600, 600);
  ellipse(600, 400, 600, 600);
  ellipse(700, 400, 600, 600);
}
```

```java
// A square and two lines

void setup() {
  size(1200, 800);
}

void draw() {
  background(#F9FAFB);

  stroke(#1C2260);
  strokeWeight(4);
  line(100, 300, 1100, 300);
  line(100, 500, 1100, 600);

  fill(#FFEA8A);
  rect(500, 300, 200, 200);
}
```

```java
// A square above a circle

void setup() {
  size(1200, 800);
}

void draw() {
  background(#F9FAFB);

  noStroke();
  fill(#DFE3E8);
  ellipse(500, 400, 300, 300);

  fill(#5C6AC4);
  rect(450, 250, 300, 300);
}
```

## Conclusion

If you understand all of the concepts above you are ready for the next level of generative design. Until now we were only building static graphic designs. We made a reflection of what Adobe Illustrator can do, only in code. You might know already that Processing is much mightier than this.

