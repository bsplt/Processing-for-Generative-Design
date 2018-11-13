## Introduction to Processing

### What is Processing?

Processing is a software that offers us a lot of possibilities that we would also find in regular graphic design software (like Adobe Illustrator). Both enable us to draw some graphics on a canvas and export it in different ways. But Processing has the power repeat different operations very quickly and use external or random data together in a defined logical way to create things that are not possible in Adobe Illustrator.

The reason behind this difference is the nature of the two: With Adobe Illustrator, we use a general purpose software which is a reflection of the design processes before computers. With Processing, we build a specialized software with the help of programming, incorporating the power of the digital. Processing calls the software pieces, that you create, *sketches*.

### It's all code

A fundamental difference between working with traditional design software and tools like Processing is, that everything you do is written in text. This text is called code because Processing makes an interpretation of that text to run its operations. You will never have draw a rectangle or bézier curve by hand. It's all written out.

### Getting Processing

You can find documentation and downloads on the official [website](https://processing.org/) of Processing.

### Is there other software like Processing?

*What* we do in Processing can be done in any widespread programming language you can probably think of. But *how* we do it is especially easy and lean in Processing. Processing is free, there is not much need for installations and Processing sketches are only one file, easy to share and uncomplicated. It also offers a lot of things we use as graphic designers, without the need to care about anything.

So Processing is an ideal starting point for generative design, especially for beginners, because we do not have to take care of all the other tedious implications that programming normally has. It is made by designers and artists for designers and artists.

### A common ground to start

I think it will be easier for designers to learn processing with the help of analogies which they can connect with their experience. This is why I will use a lot of references to Adobe Illustrator in the first paragraphs.

### The very basics of Processing

When you open Processing for the first time, you will not see much. There is an empty text editor and a big play button. Clicking on that play button will run your software, as soon as you have written some code, but first we need to define some basics.

In Adobe Illustrator, as soon as you want to create a new design document, the first thing it will show you is a prompt for your basic settings like document size and color space. This is an initial step for setting up your project and is needed, but only once in the beginning.

In Processing we have to do the same too. Processing needs some basic information, for example the size of the canvas it will create, when we run it. We have a way of defining these initial settings, that are needed, exactly once, when we start the sketch.

```java
void setup() {
    // Initial settings:
    size(800, 800);
}
```

Woah! There is a lot going on at once. All these weird parentheses ... Don't worry, at this stage you only have to care about the abstract concept behind this, which I'm trying to explain you with the help of the analogy. The rest, like `void` or these `()`, `{}` and `//` I will explain further down.

In Illustrator, as soon as you have created that document with the settings you wanted, you will get that new and empty canvas on which you can draw your vector graphics.

As you have seen above, in Processing we have to think everything in code.
