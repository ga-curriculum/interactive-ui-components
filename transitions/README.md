# ![Transitions](./assets/interactive-component-transitions.png)

**Learning objective:** By the end of this lesson, students will be able to explore CSS transitions to implement smooth, gradual visual changes between states in HTML elements, utilizing properties like transition-duration, transition-property, and transition-timing-function to control animation timing and effects.

## How Do Transitions Work?
Similar to the `transform` property, `transition`s allow us to alter the original state of an HTML element. Unlike `transform`, `transition`s are **not** static nor are they permanent. Rather, a CSS `transition` allows an element to smoothly and gradually change (or transition) between different states. While you choose the begin and end state, CSS handles the tweening (the in between states). 
>  🧠 Tweening is a term from animation. CSS animations are built on a lot of foundations and principles of animations.

Another feature of CSS is that it can utilize a computer's graphics card, which can allow for smoother transitions and animations than what JavaScript can handle. Compare these two examples:
- [Draw with JavaScript](https://codepen.io/paulirish/full/nkwKs) - if you add 100 macbooks, the animation gets kinda slow and wonky
- [Draw with CSS](https://codepen.io/paulirish/pen/LsxyF) - stays smooth


## Building a Transition
Previously we mentioned that a CSS `transition` effects a gradual change bewteeen two different states. What does this mean exactly?

In `style.css` create a CSS rule for the `.transition` element when it's being hovered over:

```css
.transition:hover {
    background-color: purple;
    margin-bottom: 10rem;
}
```
Now when you hover over the div you notice that it instantly turns purple and moves up the page. As soon as you stop hovering over the `div`, it will immediately revert back to it's original state. This an example of *state*, which refers to the condition or appearance of an HTML element at a particular moment.

Let's use the `transition` property to tell CSS to handle the tweening from the default state to the hover state. Update your `.transition` rule (not the `transition:hover`) so that it looks like this:

```css
.transition {
    background-color: white;
    height: 30vh;
    width: 30vh;
    cursor: pointer;
    transition: all 2s ease;
}
```
Let's see what happens now when we hover over the `div`. Both our color and margin gradually change over the course of 2 seconds. 

Let's update the last declaration in the rule:

```css
transition: margin 2s ease;
```

Now only our margin is transitioning gradually but the color immediately changes. What's going on?

`transition` is actually shorthand for various properties.

## Transition Properties

1. `transition`: a shorthand property for setting the other four transition properties into a single property.
1. `transition-delay`: specifies a delay (in seconds) for the transition effect.
1. `transition-duration`: specifies how many seconds or milliseconds a transition effect takes to complete.
1. `transition-property`: specifies the name of the CSS property the transition effects. 
1. `transition-timing-function`: specifies the speed curve of the transition effect. In other words, it allows you to specify the acceleration or deceleration pattern of an animation. It answers questions like:
    - How quickly does the animation start?
    - Does it start slowly and then speed up, or vice versa?
    - Does it maintain a constant speed throughout the animation?
    - Does it ease in and ease out smoothly?
    Here's a complete list of the different kinds of speed-curves your can use for this property.
In our transition declaration from above we specified the following:
- The name of the property we were transitioning
    - `all` transitions all properties
    - `margin` transitioned only the margin
- The duration of the transition. We set it to 2 seconds.
- The timing function of our animation was set to `ease`.
    - This is the most common timing function and creates a smooth, gradual transition. 
    - It starts slowly, accelerates in the middle, and slows down at the end, creating a natural and pleasing effect.
    
## Chaining Transitions
Much like `transform`, we can actually perform multiple distinct transitions in one declaration.

Let's update the `.transition` rule one more time:

```css
.transition {
    background-color: white;
    height: 30vh;
    width: 30vh;
    cursor: pointer;
    transition: margin 2s ease, background-color 1s 1s linear;
}
```

Now we have two distinct transitions occurring:
1. **Transition 1**: The margin will grow at an `ease` rate from `0` to `10rem` over the course of 2 seconds
1. **Transition 2**: The background-color will not change for 1 second. After 1 second has elapsed the background-color will change from white to purple at a `linear` rate over the course of another second.
