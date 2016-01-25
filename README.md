# Stylus background-image mixin
A Stylus mixin to manage background images.

### Dependencies
  * [stylus](https://github.com/LearnBoost/stylus)

Example:
```stylus
@import "backgroundImages"

.Div__one
 backgroundImage('image-one.jpg') 
 
.Div__two
 backgroundImage('image-two.jpg', cover, 50% 50%, clip)
 
.Div__three
  backgroundImage('image-three.jpg', 10% 10%, 0 0, repeatY)
```

Will output:
```css
.Div__one {
  background-image: url("../images/image-one.jpg");
  background-repeat: none;
}
.Div__two {
  background-image: url("../images/image-two.jpg");
  background-size: cover;
  background-position: 50% 50%;
  background-clip: clip;
  background-repeat: none;
}
.Div__three {
  background-image: url("../images/image-three.jpg");
  background-size: 10% 10%;
  background-repeat: repeat-y;
}
```

Example with Retina support and "check" option enabled for the "background-size" property:
```stylus
.Div__four
  backgroundImage('image.jpg', check, 0 0, repeatY retina, imageP = 'images')
```
Will output:
```css
.Div__four {
  background-image: url("images/image.jpg");
  background-size: 1960px 1320px;
  background-repeat: repeat-y;
}
@media only screen and (-webkit-min-device-pixel-ratio: 1.3), only screen and (min--moz-device-pixel-ratio: 1.3), only screen and (-o-min-device-pixel-ratio: 1.3/1), only screen and (min-resolution: 125dpi), only screen and (min-resolution: 1.3dppx) {
  .Div__four {
    background-image: url("images/@2ximage.jpg");
    background-size: 980px 660px;
  }
}
```

!Note:
- The "check" option will returns the width and height of the image found at the given path, the "check" in addition to the "retina" option will returns the width and height of the image divided by 2 in the @media rule.
- The "retina" option prefix the filename with "@2x".
- If you work with a lot of retina background images you should think about @extend the function.

Complete list of arguments:
- fileN: file name with extension
- size: width and height with px or %, auto, length, cover, contain, initial, inherit
- position: left top center bottom, px, %, initial, inherit
- argument: repeat, repeatY, repeatX, retina
- imageP: path to the image folder, for ex. "../images"

## Credits

Developed by [Alexis Gaillard](https://alexisgaillard.com/). Licensed under [MIT](http://opensource.org/licenses/mit-license.php).
