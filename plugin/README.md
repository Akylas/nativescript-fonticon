## A simpler way to use font icons with NativeScript

[![MIT license](http://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)
[![Dependency Status](https://david-dm.org/nativescript-community/fonticon/status.svg)](https://david-dm.org/nativescript-community/fonticon#info=dependencies) [![devDependency Status](https://david-dm.org/nativescript-community/fonticon/dev-status.svg)](https://david-dm.org/nativescript-community/fonticon#info=devDependencies)

### The Problem

You can use icon fonts with NativeScript by combining a class with a unicode reference in the view:

* CSS
```
.fa {
  font-family: FontAwesome;
}
```

* view
```
<Label class="fa" text="\uf293"></Label>
```

This works but keeping up with unicodes is not fun.

### The Solution

With this plugin, you can instead reference the `fonticon` by the specific classname:

```
<Label class="fa" text="{{'fa-bluetooth' | fonticon}}"></Label> 
```

## Install

```
npm install @nativescript-community/fonticon --save
```

### Usage

[FontAwesome](https://fortawesome.github.io/Font-Awesome/) will be used in the following examples but you can use any custom font icon collection.

* Place font icon `.ttf` file in `app/fonts`, for example:
  
```
app/fonts/fontawesome-webfont.ttf
```

* Create base class in `app.css` global file, for example:

```
.fa {
  font-family: FontAwesome, fontawesome-webfont;
}
```

**NOTE**: Android uses the name of the file for the font-family (In this case, `fontawesome-webfont`.ttf. iOS uses the actual name of the font; for example, as found [here](https://github.com/FortAwesome/Font-Awesome/blob/master/css/font-awesome.css#L8). You could rename the font filename to `FontAwesome.ttf` to use just: `font-family: FontAwesome`. You can [learn more here](http://fluentreports.com/blog/?p=176).(http://fluentreports.com/blog/?p=176).

* Copy css to `app` somewhere, for example:

```
app/font-awesome.css
```

Then modify the css file to isolate just the icon fonts needed. [Watch this video to better understand](https://www.youtube.com/watch?v=qb2sk0XXQDw).

* Configure your fonts and setup the converter:

```typescript
import * as application from '@nativescript/core/application';
import {FontIcon, fonticon} from '@nativescript-community/fonticon';

FontIcon.debug = true; <-- Optional. Will output the css mapping to console.
FontIcon.paths = {
  'fa': 'font-awesome.css',
  'ion': 'ionicons.css'
};
FontIcon.loadCss();

application.setResources( { fonticon } );
application.run({ moduleName: 'main-page' });
```

* Use the Converter, for example:

```xml
<Label class="fa" text="{{'fa-bluetooth' | fonticon}}"></Label> 
``` 

Demo FontAwesome (iOS) |  Demo Ionicons (iOS)
-------- | ---------
![Sample1](https://cdn.filestackcontent.com/m6JyRO1fTsCHPohoZi5I?v=0) | ![Sample2](https://cdn.filestackcontent.com/jje2pehCRCeLDC8QHBmp?v=0)

Demo FontAwesome (Android) |  Demo Ionicons (Android)
-------- | -------
![Sample3](https://cdn.filestackcontent.com/lNCptx2aQisOa6p27iqb?v=0) | ![Sample4](https://cdn.filestackcontent.com/2ajSF92uQDusI37fEvQA?v=0)

### Font Awesome 5

In this case, you have to copy and import each `ttf` file and associate it with the proper class:

```css
.fas {
  font-family: Font Awesome 5 Free, fa-solid-800;
}
.far {
  font-family: Font Awesome 5 Free, fa-regular-400;
}
```

but still you will import the `css` only once with the `fa` prefix:

```typescript
FontIcon.paths = {
  'fa': 'font-awesome.css'
};
```

## How about NativeScript with Angular?

If using [Angular](https://angular.io/), use this instead:

* [nativescript-ng2-fonticon](https://github.com/NathanWalker/nativescript-ng2-fonticon)

## Credits

Idea came from [Bradley Gore](https://github.com/bradleygore)'s [post here](http://www.blog.bradleygore.com/2016/03/28/font-icons-in-nativescript/).

## Contributors

- [NathanaelA](https://github.com/NathanaelA)

# License

[MIT](/LICENSE)
