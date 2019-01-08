# Advanced Drawing

## About this chapter

In the previous chapter we looked into the basic drawing capabilities of Processing. You probably know how to bring shapes to the screen in general but you are interested in how to make these drawings dynamic. Before we get to the benefit of programming design, I want to get some things out of the way.

## File Handling

Before we keep advancing in the topic of drawing in Processing, I want to address a general topic: Saving your sketch. I am pretty sure, that you are familiar with the basics of saving a file locally. Either you use `File > Save` in the Editor or you press `Ctrl + s` or `Cmd + s` respectively.

Processing will now save your code as a text file with a `.pde` suffix inside a folder that has the exact name as your sketch. This minimal footprint enables you maximum portability. You can send this file to anyone with an installation of Processing.

Later, we will add more files and folders to this directory, but the idea stays the same.

By the way, Processing excellently works inside a git-based work flow.

## The most basic interaction: Mouse movement

Generally interactions take some time and practice to be programmed. Interactions have to be precise and well defined in order to serve your purpose.

There is one interaction though that is so use to use, you almost do not have to rewrite any of the code from the last chapter to make it dynamic.

Instead of using fixed numbers, we can use `mouseX` and  `mouseY` to bind values to our movement.

For example instead of writing this:

```java
line(100, 100, 700, 700);
```

we could do this:

```java
line(100, 100, mouseX, mouseY);
```

Now  Processing will not draw the line between to static points anymore but between one fixed point and the cursor of your mouse.

You can use this technique mostly in every command that requires you to put in coordinates, dimensions or numbers of all sorts.

Implicitly the topic we are covering here is variables.  You will read about this in the next chapter. What is interesting about  `mouseX` and `mouseY` though is the concept of using  a symbol (by typing out `mouseX` for examples) that acts as a placeholder for a value. In this case Processing is taking care of this value and updates the position of your mouse automatically. This will be a key concept later on.

## Responsive layouts: Using the width and height of the sketch

Sometimes you know exactly for which display you are designing and developing. In this case it is absolutely fine just to use pixel values for everything.  If you consider running your sketch on more than a known display with a fixed resolution, for example when you want to share your code, you should just use relative values to describe positions and dimensions. You might know a similar technique from web design.

The problem we have is the variety of display resolutions we might find in practice. A window with the resolution `size(800, 800)` will look okay on a FullHD-Display, but will look tiny on a 4K-Display. So if you increase the size, you also want the content to scale accordingly. This will not happen, if you use absolute values.

This is an example for problematic code:

```java
rect(200, 200, 400, 400);
```

The solution is easy and straightforward. You can derive positions and dimensions from the size of the window itself. Similar to the case we  looked at above (`mouseX` and `mouseY`), Processing takes care of this. We can use `width` and `height`, two variables that are set by Processing automatically. The values in the variables will correspond to the  values you have put into the `size()` command.

A responsive translation of the code above would look like this:

```java
rect(width * 0.25, height * 0.25, width * 0.5, height* 0.5);
```

By multiplying `width` and `height` width numbers between 0 and 1 you will get fractions of the window size. So in the exemplary case above the rectangle will always  fill half of your window, (`width * 0.5`) no matter how big it is in pixel values.

This is how a whole sketch might look like:

```java
void setup() {
    size(800, 800);
}

void draw() {
    rect(width * 0.25, height * 0.25, width * 0.5, height* 0.5);
    ellipse(width * 0.5, height * 0.5, width * 0.5, width * 0.5);
    line(width * 0.25, height * 0.5, width * 0.75, height * 0.5);
}
```

If you have further interested in this topic, I will tell you another trick. It is a bit more advanced though, so you could consider skipping this part.

By using both `min()` and `max()` you have an option to compare two values and either chose the bigger or smaller value. For example `max(200, 400)` will result into `400` because it is the bigger of the two values.

If you look at the example above, you can see that in the line `ellipse(width * 0.5, height * 0.5, width * 0.5, width * 0.5);` I was using two times the exact same relative value for the width and height of the ellipse, which is `width * 0.5`. The reason, which might  not be so obvious at first sight,  is that I wanted to draw a circle, but if I had used `width` for width and ```height``` for height  of the ellipse it would not have become a circle, if the window is not square.

We can go one step further and use  `min(width, height)` or `max(width, height)` to be sure that positions or dimensions  will always fit our spatial relative requirements.

Let me give you an example:

```java
void setup() {
    size(400, 800);
}

void draw() {
    ellipse(width * 0.5, height * 0.5, min(width, height), min(width, height));
}
```

No matter how you change the values in `size()` you will always see a circle that fits exactly into the window.

## Shapes

Primitive shapes like rectangles or ellipses are great elements for minimalistic compositions. Sometimes we need more parameters to describe a form though in order to create more complex elements.

If you think about Adobe Illustrator, you would use the path tool to create connected shapes or splines. Again, Processing offers us a tool that works quite similar. We can define shapes manually with a certain set of commands, that reminds us of the functionality of the equivalent from Adobe.

To make a shape, we have two essentials commands, `beginShape()` and `endShape()`.  These two encapsulate the whole  spatial definition of the shape. Two define the shape itself we use a set of vertices. The most simple command is `vertex()`. A vertex is a point of the definition of a shape. For example, a rectangle consists of four vertices, one for each corner. So If you would draw a rectangle with `vertex()` instead of `rect()` it would look like this:

```java
void setup() {
    size(800, 800);
}

void draw() {
    beginShape();
    vertex(200, 200);
    vertex(600, 200);
    vertex(600, 600);
    vertex(200, 600);
    endShape(CLOSE);
}
```

This examples illustrates how you have to use `beginShape()` and `endShape()` to surround the vertices (`vertex()`) in order to draw a shape. You might have noticed, that `vertex()` takes two commands, the horizontal and the vertical value of the points you want to connect. If you follow along these values in your head you see that they describe a square clockwise. You might also see, that we do not close the shape manually, because the last vertex does not have the same coordinates as the first one.  In order not to have to write the same vertex in the beginning and in the end, because it feels unintuitive, Processing helps us with the `CLOSE` parameter inside `endShape()`.

There are other types of vertices, which will not result in linear connections between the points but are displayed as curves. In Illustrator you would use Bézier curves (also called cubic splines) to create curvy paths in a shape. Processing is able to do the same by using `bezierVertex()`. A lot is written about Bézier curves on the Internet so I will keep it brief. Bézier curves are described by a start and an end point, called anchor points. The curve between the two anchor points is described by two control points. If you do not know the concept yet, I would advise you to open Illustrator, draw a curve and drag around the points until you have some kind of intuition for the principle.

In the previous chapter I have told you that a command called `bezier()` exists. It works through putting in all of the points above in this order: anchor point 1, control point 1, control point 2, anchor point 2. It might look like: `bezier(100, 100, 600, 100, 600, 600, 100, 600);`

The `bezierVertex()` command works a bit different because the second anchor point of a curve is always the first anchor point of the next curve. In order to assure this Processing skips the first anchor point completely. The order is now: control point 1, control point 2, anchor point 2. It might look like: `bezierVertex(600, 100, 500, 600, 100, 600);`. We compensate for the missing first anchor point of the first curve with a regular `vertex()`. This is an example for the usage of Bézier curves:

```java
void setup() {
    size(800, 800);
}

void draw() {
    beginShape();
    vertex(200, 400);
	bezierVertex(200, 100, 600, 100, 600, 300);
    bezierVertex(600, 400, 600, 400, 600, 500);
    bezierVertex(600, 700, 200, 700, 200, 400);
    endShape(CLOSE);
}
```

There is a similar command for simpler curves (quadratic curves) called `quadraticVertex()`, which works the same way, only with one control point. Processing also offers Catmull-Rom splines with `curveVertex()`. In both cases, if you are interested, I would recommend to check out the Processing documentation.

## Text

todo

## Randomness

todo

## Examples to illustrate the previously learned

todo

## Conclusion

todo