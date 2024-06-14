# ![Animations](./assets/interactive-components-animations.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

## How Do Animations Work?
Similar to CSS transitions, animations also allow us to alter the original state of an HTML element. However, unlike transitions, CSS animations are dynamic and can create continuous, fluid motion rather than just simple state changes. Animations are ideal for more complex and long-lasting effects, such as rotating a spinning wheel or creating a bouncing animation.


### Keyframes
- In CSS animations, you define something called *keyframes* that specify the intermediate states the element should go through during the animation. 
- These keyframes describe how the element should change over time, giving you precise control over the animation's behavior. 
- CSS takes care of interpolating the element's properties between these keyframes, creating the appearance of smooth motion.


## Building an Animation
An animation is not simply a transition between two element states. Rather, it is numerous transitions over a set time. 

Let's use PowerPoint as an example. In PowerPoint, you can *transition* in between slides, and then *animate* an element to fly around the page. To transition between slides you simply select the page transition you want to use. However to create an animation you might need to draw a path for your element to follow and define other criteria. 

Like our example above, with CSS there's more to building out an animation than there is to creating a transition - simply because an animation can do more.


### At-rules & `@keyframes`
CSS has something called *at-rules*. An at-rule is a special type of CSS rule that starts with the "@" symbol followed by a keyword. At-rules are used to convey instructions and information to the CSS processor and define various aspects of how styles are applied to elements on a web page. 

We've used at-rules before for media queries:

```css
@media screen and (max-width: 600px) {
    /* CSS declarations for screens with a width less than 600px */
}
```

and importing fonts:

```css
@font-face {
    font-family: 'CustomFont';
    src: url('custom-font.woff2') format('woff2');
}
```

For animations we use another at-rule: `@keyframes`. As we learned above, keyframes refers to the intermediate states the element should go through during the animation. Here's what an `@keyframes` rule looks like:

```css
@keyframes my-animation {
    /* Keyframes go here */
}
```

Let's build a simple `@keyframes` rule in our `main.css` file:

```css
@keyframes color-change {
    from {
        background-color: darkred;
    }
    to {
        background-color: purple;
    }
}
```

This is a simplistic animation with only two keyframes. Let's break them down
- `from`: This keyframe specifies the starting point of the animation, denoted as `from`. At the beginning of the animation, the `background-color` property is set to `darkred`. This is the initial state or style.
- `to`: This keyframe defines the ending point of the animation, denoted as `to`. As the animation progresses to completion, the background-color property gradually transitions to purple. This represents the final state or style.


## Implementing an Animation
Now that we've built our animation, it's time to use it! We can use the CSS property `animation` to apply a defined animation to a HTML elements. In the `.animation` rule add this declaration:
```css
animation: color-change 3s linear infinite alternate
```
Go back to the browser and take a look at what's happening! Our `.animation` div is now continuously changing colors - without any need for user interaction! This is just a taste of the power of animations :fire:

## Animation Properties
Animations have all the same properties that transitions do, as well as many more! Here's a complete list of all the animation properties you can use:
- `animation`: a shorthand property for setting all the animation properties
- `animation-delay`: specifies a delay for the start of an animation
- `animation-direction`: specifies whether an animation should be played forwards, backwards or in alternate cycles
- `animation-duration`: specifies how long time an animation should take to complete one cycle
- `animation-fill-mode`: specifies a style for the element when the animation is not playing (before it starts, after it ends, or both)
- `animation-iteration-count`: specifies the number of times an animation should be played
- `animation-name`: specifies the name of the `@keyframes` animation
- `animation-play-state`: specifies whether the animation is running or paused
- `animation-timing-function`: specifies the speed curve of the animation
In our animation declaration from above we specified the following:
- The name of the `@keyframes` animation we were using - `color-change`
- The duration of the transition. We set it to 3 seconds.
- The timing function of our animation was set to `linear`. 
    - The animation progresses at a constant speed throughout its duration. 
    - There is no acceleration or deceleration, resulting in a constant and uniform motion.
- The iteration count of our animation was set to infinite, meaning the animation will continuously loop.
- The direction in which the animation follows the keyframes. We told the animation to alternate between running forwards and backwards.

## Chaining Animations
We can chain animations in the same way we chain transitions! Let's go ahead and build a second (more complex) animation that we can chain on to our previous one.
Here's the `@keyframes` rule:

```css
@keyframes around-the-world {
    0% {
        top: 0;
        left: 0;
    }
    25% {
        top: calc(100% - 30vh);
        left: 0;
    }
    50% {
        top: calc(100% - 30vh);
        left: calc(100% - 30vh);
    }
    75% {
        top: 0;
        left: calc(100% - 30vh);
    }
    100% {
        top: 0;
        left: 0;
    }
}
```

- With animations using more than two keyframes you need to use percentages to indicate at which stage of the aniamtion will a specific keyframe's styles be implemented.
- This animation will move the *animation* div around the border of the *container* div. Here's a breakdown of what each keyframe is doing:
    - At the start of the animation (0% progress), the element is positioned at the top-left corner of the container.
    - When the animation reaches 25% progress, the element's moves to the bottom of the container. The left property remains 0, so the element is at the bottom-left corner.
    - At the halfway point of the animation (50% progress), the element's top position remains at the bottom of the screen but moves to the bottom-right corner.
    - As the animation reaches 75% progress, the element's top position is reset to 0, moving it to the top-right corner of the screen.
    - Finally, when the animation is complete (100% progress), both the top and left properties are reset to 0, returning the element to the top-left corner of the screen.


Now that we built out our keyframes, let's chain it on to our previous animation! We'll also need to update some intial styles of the `.animation` div so that when the page loads it starts out in the top-left corner of the container.

```css
.animation {
    background-color: darkred;
    height: 30vh;
    width: 30vh;
    cursor: pointer;
    border-radius: 50%;
    animation: color-change 3s linear infinite alternate, around-the-world 10s linear infinite forwards;
    position: absolute;
    top: 0;
    left: 0;
}
```

We now have two animations running simultaneously:
1. **color-change**: The div alternates between two colors every 3 seconds
1. **around-the-world**: The same div completely circumnavigates the container every 10 seconds