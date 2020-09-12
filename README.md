# CSSMarquee
**CSSMarquee** is a Javascript no dependencies javascript marquee based on CSS animations.

Core features of **CSSMarquee** are:

## Installation

**CSSMarquee** is registered as a package on [npm](https://www.npmjs.com/package/zpt). This is the recomended way of downloading it. You can install the latest version of CSSMarquee and its dependencies with the npm CLI command:

```bash
npm install css-marquee
```
As an alternative you can download from [github](https://github.com/davidcana/CSSMarquee/archive/master.zip).

## Usage

*cssMarqueExample.html*

```html
<!DOCTYPE HTML>
<html>

<head>
  <meta charset="utf-8">
  <link rel="stylesheet" type="text/css" href="style.css">
  <script src="cssMarquee.min.js"></script>
  <title>CSSMarquee</title>
</head>

<body>
    <p id="myMarquee" class="marquee">Default text</p>
    
    <script>
        var myMarquee = new CSSMarquee({
            id: 'myMarquee',
            text: 'CSSMarquee: no dependencies javascript marquee based on CSS animations.',
            speed: 20,
            pauseOnMouseEnter: true,
            playOnMouseLeave: true
        });
    </script>
</body>

</html>
```

Where **cssMarquee.min.js** is the minimized version of cssMarquee.

Available configuration parameters are:

*  **id**. The id of the DOM element.
*  **element**. The DOM element. It is required to set **element** or **id**. If both are set **element**is used.
*  **text**. The text in the marque. If it is not set CSSMarquee uses the text in the DOM element. It is required to set **text** or some text in the DOM element.
*  **speed**. The number of seconds to complete one iteration. Default is 15.
*  **pauseOnMouseEnter**. If it is true the animation will be paused when a **mouseenter** event is triggered.
*  **playOnMouseLeave**. If it is true the animation will be resumed when a **mouseleave** event is triggered.
*  **animation**. The CSS animation to use. Default is **marqueeTextIndent {0}s linear infinite**. See the next chapter for more details.

Available methods for **CSSMarquee** instances are:
*  **pause()**. Pauses the animation.
*  **play()**. Resumes the animation.
*  **updateText( newText )**. Updates the text.
*  **destroy( removeText )**. Stops the animation and remove all listeners. If **removeText** removes the text of the marquee.


Go to [test page](https://davidcana.github.io/CSSMarquee) to see **CSSMarquee** in action!

## Customizing the CSS animation

If you want to fully customize the CSS animation keep on reading this!

Default **animation** is **marqueeTextIndent {0}s linear infinite**. You can customize it with the built in keyframes CSS animations or define a new one. The **{0}** part is replaced by **CSSMarquee** with the **speed** configuration parameter.

**CSSMarquee** includes 4 keyframes CSS animations in the **style.css** file:

*  **marqueeTextIndent** (used in default animation). Animates the **text-indent** property. Animation is from right to left.
*  **marqueeTextIndentReverse**. Animates the **text-indent** property. Animation is from left to right.
*  **marqueeTranslateX**. Uses **translateX** to animate. Animation is from right to left.
*  **marqueeTranslateXReverse**. Uses **translateX** to animate. Animation is from left to right.

The definitions of both in the **style.css** file are:

```css
@keyframes marqueeTextIndent {
    0%   { text-indent: 100% }
    100% { text-indent: var(--marquee-text-size) }
}

@keyframes marqueeTextIndentReverse {
    0%   { text-indent: var(--marquee-text-size)  }
    100% { text-indent: 100% }
}

@keyframes marqueeTranslateX {
    0%   { transform: translateX( 100% ) }
    100% { transform: translateX( var(--marquee-text-size) ) }
}

@keyframes marqueeTranslateXReverse {
    0%   { transform: translateX( var(--marquee-text-size) ) }
    100% { transform: translateX( 100% ) }
}
```

The **--marquee-text-size** CSS variable is set by **CSSMarquee**. Its value depends on the length of the text to animate.

Of course, if you are not going to use one of them you do not need to include it in you CSS files.

Another option is to define a new keyframes CSS animation in one of your CSS files and customize the **animation** option to use it.

## License
[LGPL](http://www.gnu.org/licenses/lgpl.html)
