# sass-mediaqueries

It's a collection of useful **Media Queries** mixins for **Sass** (including iOS devices, TVs and more). Fully customizable and very easy to use.

#### Online: <http://paranoida.github.com/sass-mediaqueries>

### How to install:

1. Using **bower**: 

	```
	bower install sass-mediaqueries --save-dev
	```

	Or manually using **curl**:

	```
	curl -O https://raw.github.com/paranoida/sass-mediaqueries/master/_media-queries.scss
	```

2. After that, at the top of your sass/scss file (ie. `application.scss`) add:

	```
	@import "media-queries";
	```

## Doc:

#### Config (default):

##### $mq-tablet: `1024px !default`
	
Default breakpoint for tablets

##### $mq-mobile: `768px !default`
	
Default breakpoint for mobiles devices

##### $mq-mobile-first: `false !default`

With this switch you can control which approach do you want to use.


#### Mixins:

```
@* desktop(mobile-first)
@* tablet(mobile-first)
@* mobile(mobile-first)
--
@  screen(min-width, max-width, orientation)
@  min-screen(width)
@  max-screen(width)
--
@  screen-height(min-height, max-height)
@  min-screen-height(height)
@  max-screen-height(height)
--
@  iphone3(orientation)
@  iphone4(orientation)
@  iphone5(orientation)
--
@  ipad(orientation)
@  ipad-retina(orientation)
--
@  hdpi(ratio)
--
@  hdtv(standard) - beta
```

** NOTE: ** mixins marked with `*`, depend on `$mq-mobile-first` state

---

#### - desktop($mobile-first: $mq-mobile-first)

It targets desktops or every device which screen resolution is greather than default tablet breakpoint.

#### - tablet($mobile-first: $mq-mobile-first)

It targets default tablet breakpoint.

#### - mobile($mobile-first: $mq-mobile-first)

It targets default mobile breakpoint.

###### # Example (mobile-last):

```
// $mq-mobile-first has default value (false)

.box {
	width: 600px;
	
	@include tablet {
		width: 50%;
	}
	@include mobile {
		width: 100%;	
	}
}
```

###### # Example (mobile-first):

```
$mq-mobile-first: true;

.box {
	width: 100%;
	
	@include tablet {
		width: 50%;
	}
	@include desktop {
		width: 600px;	
	}
}
```

---

#### - screen($min-width, $max-width, $orientation: false)

It targets group of devices or just one with particular screen resolution and orientation (optional).

###### # Example:

```
@include screen(320px, 640px)  { ... }
@include screen(768px, 1024px, landscape) { ... }
```

It will be compiled to:

```
@media screen and (min-width: 768px) and (max-width: 1280px) { ... }
@media screen and (min-width: 320px) and (max-width: 640px) and (orientation: landscape) { ... }
```

#### - min-screen($width)

It's a shortcut for `@media screen and (min-width ... )`

###### # Example:

```
@include min-screen(768px)  { ... }
@include min-screen(1024px) { ... }
```

It will be compiled to:

```
@media screen and (min-width: 768px)  { ... }
@media screen and (min-width: 1024px) { ... }
```


#### - max-screen($width)

It's a shortcut for `@media screen and (max-width ... )`

###### # Example:

```
@include max-screen(1024px) { ... }
@include max-screen(768px)  { ... }
```

It will be compiled to:

```
@media screen and (max-width: 1024px)  { ... }
@media screen and (max-width: 768px)   { ... }
```

---

#### - screen-height($min-height, $max-height)



###### # Example:

```
@include screen-height(640px, 768px)  { ... }
```

It will be compiled to:

```
@media screen and (min-height: 768px) and (max-height: 1280px) { ... }
```

#### - min-screen-height($width)

It's a shortcut for `@media screen and (min-height ... )`

###### # Example:

```
@include min-screen-height(768px)  { ... }
@include min-screen-height(1024px) { ... }
```

It will be compiled to:

```
@media screen and (min-height: 768px)  { ... }
@media screen and (min-height: 1024px) { ... }
```


#### - max-screen-height($width)

It's a shortcut for `@media screen and (max-height ... )`

###### # Example:

```
@include max-screen-height(1024px) { ... }
@include max-screen-height(768px)  { ... }
```

It will be compiled to:

```
@media screen and (max-height: 1024px)  { ... }
@media screen and (max-height: 768px)   { ... }
```

---

```
$orientation: all | portrait | landscape
```

#### - iphone3($orientation: all)

It targets only **iPhone 3** + orientation

#### - iphone4($orientation: all)

It targets only **iPhone 4** + orientation

#### - iphone4($orientation: all)

It targets only **iPhone 5** + orientation

#### - ipad($orientation: all)

It targets all **iPads** + orientation

#### - ipad-retina($orientation: all)

It targets only **iPads with retina** display + orientation

###### # Example:

```
@include ipad { ... }                 // all iPads
@include ipad-retina { ... }          // only iPad with retina

@include iphone5 { ... }              // only iPhone 5
@include iphone4 { ... }              // only iPhone 4/4S
@include iphone3 { ... }              // only iPhone 2/3G/3GS
```

###### # Example:

```
// common part for iPhone 5 - landscape & portrait
@include iphone5 { ... } 

@include iphone5(landscape) { ... }
@include iphone5(portrait)  { ... }
```

---

#### - hdpi($ratio: 1.3)

###### # Example:
```
.brand {
	background-image: url(logo.png);
	
	@include hdpi {
		background-image: url(logo_2x.png);
	}
}
```
---

```
$standard: '720p' | '1080p' | '2K' | '4K'
```

#### - hdtv($standard: '1080p') - beta

It targets TVs with particular standard like `1080p` or `4K`

###### # Example:
```
.title {
	font-size: 5vm;
	
	@include hdtv {
		font-size: 10vm;
	}
	
	@include hdtv('4K') {
		font-size: 15vm;
	}	
}
```

---

### Credits:

You can check my <a href="http://paranoida.com">website</a> or follow me on <a href="https://twitter.com/paranoida">twitter</a>.

---

### License:

The MIT license

Copyright &copy; 2013 [Rafal Bromirski](http://paranoida.com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.