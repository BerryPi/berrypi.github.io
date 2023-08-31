---
title: CSS Animation
---
### Setting Animation Progress
JavaScript can be used to change how far an DOM element is into its animation by changing its `animation-delay` property. 
If this is negative, then the animation will start out as if that amount of time has already passed.  
E.g. `animation-delay: -2s;` will style an element as how it would look 2 seconds after the start of the animation.

If what you want to do is the sensible thing of setting a percentage progress through the animation, then you'll need to multiply that percentage by the animation duration.

`animation-delay: calc(-1 * --animation-progress * --animation-duration);`

### Resetting Animation Progress
To put an element back to its position from when the page was loaded, setting `animation-delay: 0;` won't necessarily work as it may have started out with a delay.

Instead, you can remove the CSS class/id that provides the animation from the element, access a property on it that triggers reflow, then add the class/id back in.

[Sample on StackOverflow](https://stackoverflow.com/a/45036752)