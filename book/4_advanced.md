# Advanced Drawing

## About this chapter

In the previous chapter we looked into the basic drawing capabilities of Processing. You probably know how to bring shapes to the screen in general but you are interested in how to make these drawings dynamic. Before we get to the benefit of programming design, I want to get some things out of the way.

## File Handling

Before we keep advancing in the topic of drawing in Processing, I want to address a general topic: Saving your sketch. I am pretty sure, that you are familiar with the basics of saving a file locally. Either you use ```File > Save``` in the Editor or you press ```Ctrl + s``` or ```Cmd + s``` respectively.

Processing will now save your code as a text file with a ```.pde``` suffix inside a folder that has the exact name as your sketch. This minimal footprint enables you maximum portability. You can send this file to anyone with an installation of Processing.

Later, we will add more files and folders to this directory, but the idea stays the same.

By the way, Processing excellently works inside a git-based work flow.

## The most basic interaction: Mouse movement

Generally interactions take some time and practice to be programmed. Interactions have to be precise and well defined in order to serve your purpose.

There is one interaction though that is so use to use, you almost do not have to rewrite any of the code from the last chapter to make it dynamic.

Instead of using fixed numbers, we can use ```mouseX``` and  ```mouseY``` to bind values to our movement.

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

Implicitly the topic we are covering here is variables.  You will read about this in the next chapter. What is interesting about  ```mouseX``` and ```mouseY``` though is the concept of using  a symbol (by typing out ```mouseX``` for examples) that acts as a placeholder for a value. In this case Processing is taking care of this value and updates the position of your mouse automatically. This will be a key concept later on.

## Responsive layouts: Using the width and height of the sketch

Sometimes you know exactly for which display you are designing and developing. In this case it is absolutely fine just to use pixel values for everything.  If you consider running your sketch on more than a known display with a fixed resolution, for example when you want to share your code, you should just use relative values to describe positions and dimensions. You might know a similar technique from web design.

The problem we have is the variety of display resolutions we might find in practice. A window with the resolution ```size(800, 800)``` will look okay on a FullHD-Display, but will look tiny on a 4K-Display. So if you increase the size, you also want the content to scale accordingly. This will not happen, if you use absolute values.

This is an example for problematic code:

```java
rect(200, 200, 400, 400);
```

The solution is easy and straightforward. You can derive positions and dimensions from the size of the window itself. Similar to the case we  looked at above (```mouseX``` and ```mouseY```), Processing takes care of this. We can use ```width``` and ```height```, two variables that are set by Processing automatically. The values in the variables will correspond to the  values you have put into the ```size()```-command.

A responsive translation of the code above would look like this:

```java
rect(width * 0.25, height * 0.25, width * 0.5, height* 0.5);
```

By multiplying ```width``` and ```height``` width numbers between 0 and 1 you will get fractions of the window size. So in the exemplary case above the rectangle will always  fill half of your window, (```width * 0.5```) no matter how big it is in pixel values.

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

By using both ```min()``` and ```max()``` you have an option to compare two values and either chose the bigger or smaller value. For example ```max(200, 400)``` will result into ```400``` because it is the bigger of the two values.

If you look at the example above, you can see that in the line ```ellipse(width * 0.5, height * 0.5, width * 0.5, width * 0.5);``` I was using two times the exact same relative value for the width and height of the ellipse, which is ```width * 0.5```. The reason, which might  not be so obvious at first sight,  is that I wanted to draw a circle, but if I had used ```width``` for width and ```height``` for height  of the ellipse it would not have become a circle, if the window is not square.

We can go one step further and use  ```min(width, height)``` or ```max(width, height)``` to be sure that positions or dimensions  will always fit our spatial relative requirements.

Let me give you an example:

```java
void setup() {
    size(400, 800);
}

void draw() {
    ellipse(width * 0.5, height * 0.5, min(width, height), min(width, height));
}
```

No matter how you change the values in ```size()``` you will always see a circle that fits exactly into the window.

## Shapes

Primitive shapes like rectangles or ellipses are great elements to start with. Sometimes we need more parameters to describe a form though in order to great more complex elements.

## Text

## Randomness

## Examples to illustrate the previously learned

## Conclusion