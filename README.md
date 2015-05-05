# Compass Sprites

In order to use this mixin, I consume that you are already familiar with [Compass](http://compass-style.org/) and it's [Spriting](http://compass-style.org/help/tutorials/spriting/) feature.

What this mixin does, is that, it uses CSS Contains Selector, which is [supported by every major browser](http://caniuse.com/#feat=css-sel3), including IE7 and above, rather than adding each class name to CSS, which represents the sprite file name.

For example, this code:

```css
.icon, .icon-home, .icon-info, [class*="icon-"] {
  background-image: url('/images/icon-se150f5a3ac.png');
  background-repeat: no-repeat;
}
```

Becomes to this:
```css
.icon, [class*="icon-"] {
  background-image: url('/images/icon-se150f5a3ac.png');
  background-repeat: no-repeat;
}
```

*When using few icons, it's not a big issue to use default spriting mixin from Compass, but if you have a lot of icons, debugging of HTML/CSS can be one hell of a process.*


# Installation

You can manually create `_sprites.scss` file and paste the contents of the [_sprites.scss](https://github.com/Landish/compass-sprites/blob/master/_sprites.scss) file in it.

Or you can install with [Bower](http://bower.io):

```
bower install compass-sprites --save
```

# Usage

Let's consider the following scenratio, where you have initialised Compass in your project with `compass init` command.

Create a `/sass/_icons.scss` file and fill it with the following content: 

( Example code can be found [here](https://github.com/Landish/compass-sprites/blob/master/_icons.example.scss) )

```scss
$icon-sprite-dimensions: true;
$icon-layout: smart;
$icon-sprite-base-class: '.icon';
@import "icon/*.png";
@include all-icon-sprites;

[class*="icon-"] {
  @extend .icon;
  display: inline-block;
  vertical-align: middle;
}
```

In your `/sass/screen.scss` file after importing `compass` import `sprites` mixin and `icons`:

```scss
@import "compass";
@import "sprites";
// or if you have installed it with bower:
// @import "path/to/bower_components/compass-sprites/sprites";
@import "icons";
```

**Note: If you don't import `sprites`, compass will use default spriting mixin for generating sprites.**

Place some icons/images into your `/images/icon/` directory and run the `compass compile` or `compass watch` command.

You can also compile Compass with [Gulp](http://gulpjs.com/), [Grunt](http://gruntjs.com/) or any other 3rd-party applications, such as [Prepros](https://prepros.io/) or [Koala](http://koala-app.com/). 

After compiling Compass into CSS, you can use the following syntax of code for displayng icons in your HTML:

```html
<i class="icon-{filename}"></i>
```

Example:
```html
<i class="icon-home"></i>
<i class="icon-info"></i>
```

# License

The Compass Sprite Mixin is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).


