# CSSMarquee
**CSSMarquee** is a Javascript no dependencies javascript marquee based on CSS animations.

Core features of **CSSMarquee** are:

## Installation

**CSSMarquee** is registered as a package on [npm](https://www.npmjs.com/package/zpt). This is the recomended way of downloading it. You can install the latest version of CSSMarquee and its dependencies with the npm CLI command:

```bash
npm install cssMarquee
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
<ul>
    <li><strong>id</strong>. The id of the DOM element.</li>
    <li><strong>element</strong>. The DOM element. It is required to set <strong>element</strong> or <strong>id</strong>. If both are set <strong>element</strong>is used.</li>
    <li><strong>text</strong>. The text in the marque. If it is not set CSSMarquee uses the text in the DOM element. It is required to set <strong>text</strong> or some text in the DOM element.</li>
    <li><strong>speed</strong>. The number of seconds to complete one iteration. Default is 15.</li>
    <li><strong>pauseOnMouseEnter</strong>. If it is true the animation will be paused when a <em>mouseenter</em> event is triggered.</li>
    <li><strong>playOnMouseLeave</strong>. If it is true the animation will be resumed when a <em>mouseleave</em> event is triggered.</li>
    <li><strong>animation</strong>. The CSS animation to use. Default is <em>marqueeTextIndent {0}s linear infinite</em>. See the next chapter for more details.</li>
</ul>

Available methods for **CSSMarquee** instances are:
<ul>
    <li><strong>pause()</strong>. Pauses the animation.</li>
    <li><strong>play()</strong>. Resumes the animation.</li>
    <li><strong>updateText( newText )</strong>. Updates the text.</li>
    <li><strong>destroy( removeText )</strong>. Stops the animation and remove all listeners. If <em>removeText</em> removes the text of the marquee.</li>
</ul>

Go to [test page](https://davidcana.github.io/CSSMarquee) to see **CSSMarquee** in action!

## Customizing the CSS animation

If you want to fully customize the CSS animation keep on reading this!

Default <strong>animation</strong> is <em>marqueeTextIndent {0}s linear infinite</em>. You can customize it with the built in keyframes CSS animations or define a new one. The <em>{0}</em> part is replaced by **CSSMarquee** with the <strong>speed</strong> configuration parameter.

**CSSMarquee** includes 2 keyframes CSS animations in the **style.css** file:
<ul>
    <li><strong>marqueeTranslateX</strong>. Uses <em>translateX</em> to animate.</li>
    <li><strong>marqueeTextIndent</strong> (default). Animates the <em>text-indent</em> property.</li>
</ul>

The definitions of both in the **style.css** file are:

```css
@keyframes marqueeTranslateX {
    0%   { transform: translateX( 100% ) }
    100% { transform: translateX( var(--marquee-text-size) ) }
}

@keyframes marqueeTextIndent {
    0%   { text-indent: 100% }
    100% { text-indent: var(--marquee-text-size) }
}
```

The <strong>--marquee-text-size</strong> CSS variable is set by **CSSMarquee**. Its value depends on the length of the text to animate.

Of course, if you are not going to use one of them you do not need to include it in you CSS files.

Another option is to define a new keyframes CSS animation in one of your CSS files and customize the <strong>animation</strong> option to use it.

## License
[LGPL](http://www.gnu.org/licenses/lgpl.html)
