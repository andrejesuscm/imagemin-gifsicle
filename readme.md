# imagemin-gifsicle

> This is an hard fork of the repo [imagemin-gifsicle](https://github.com/imagemin/imagemin-gifsicle) v6.0.1

> Imagemin plugin for [Gifsicle](https://www.lcdf.org/gifsicle/)


## Install

```
$ npm install imagemin-gifsicle
```


## Usage

```js
const imagemin = require('imagemin');
const imageminGifsicle = require('imagemin-gifsicle');

(async () => {
	await imagemin(['images/*.gif'], 'build/images', {
		use: [
			imageminGifsicle()
		]
	});

	console.log('Images optimized');
})();
```


## API

### imageminGifsicle(options?)(buffer)

Returns a `Promise<Buffer>` with the optimized image.

#### options

Type: `object`

##### interlaced

Type: `boolean`<br>
Default: `false`

Interlace gif for progressive rendering.

##### optimizationLevel

Type: `number`<br>
Default: `1`

Select an optimization level between `1` and `3`.

> The optimization level determines how much optimization is done; higher levels take longer, but may have better results.

1. Stores only the changed portion of each image.
2. Also uses transparency to shrink the file further.
3. Try several optimization methods (usually slower, sometimes better results)

##### colors

Type: `number`

Reduce the number of distinct colors in each output GIF to num or less. Num must be between 2 and 256.

#### Scale

Type: `decimal`

Scale the output GIF’s width and height by Xfactor and Yfactor. If Yfactor is not given, it defaults to Xfactor. Scaling happens after all input frames have been combined and before optimization. Decimal 0.1 to 1.

### resizeWidth

Type: `number`

Resize to a given width in pixels, preserving aspect ratio.


#### buffer

Type: `Buffer`

Buffer to optimize.
