# ![Transform](./assets/interactive-ui-component-transform.png)

**Learning objective:** By the end of this lesson, students will be able to practice the CSS transform property of various visual transformations, including translate, rotate, scale, and skew, to HTML elements. 

The CSS `transform` property is a versatile property used to apply different kinds of visual transformations to HTML elements. The value of `transform` can be any number of transformation functions. You can check out the complete list of transformation functions [here](https://developer.mozilla.org/en-US/docs/Web/CSS/transform#syntax).

For now, we'll look at just four functions:
1. `translate()` 
1. `rotate()`
1. `scale()`
1. `skew()`

In `index.html`, you'll see a black-colored `div` with the class name `transform`. In the `stlye.css` add to the `.transform` class:

```css
transform: translate(500px)
```

Refresh your browser to see the changes. Depending on your screen size, your black `div` may be overlapping the white `div`. Now try:

```css
transform: translate(500px, 500px)
```
Now the black `div` is outside the border of the `.container` `div`. What's great about the `transform` property is that only the element being transformed will be affected, no other element will be affected in any way whatsoever.

Update your `transform` property using each code block below and see what happens with each transformation:

```css
transform: rotate(45deg)
```
```css
transform: scale(2)
```
```css
transform: scale(.2)
```
```css
transform: skew(20deg)
```

Awesome! Let's try multiple transformations all at once:

```css
transform: rotate(45deg) translate(100px, 100px) scale(.5);
```

As we can now see, `transform` is a great property to use to create an imemdaite and permanent transformation to an HTML element without impacting any other elements on the page. Just a few notes about syntx before we move on:

- Watch your units! 
    - `skew` and `rotate` use `deg`
    - `translate` takes `px` or `em`
    - `scale` takes no units

- There cannot be a space between the function name and the first paranthesis. These will not work:
    - `skew (25deg)`
    - `skew(25deg)`