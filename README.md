## p5.start2d.js

p5.start2d.js is an extension to ease the creation of 2D STatic ART with p5.js.
With p5.start2d.js you can use pixels (px), millimeters (mm), centimeters (cm) and
inches (in). Panning and zooming is also available, together with easy PNG file export.
Just include p5 and p5.start2d.js in your html file and you are good to go.

<p align="center">
    <img src="./assets/example-export.png" style="margin: 3em 0 2em;">
</p>

## Before using this extension, keep in mind that :
* It is created to use as a quick boilerplate for the creation of sketches which has to be exported.
* It is only tested in latest chrome / firefox.
* If p5.js didn't exist I would never have written this extension.

---

### WHILE RUNNING :

- use mouse wheel to zoom in/out

- use mouse left button to drag / pan

- use the following keys :

  - (1) : zoom canvas to real size
  - (M) : zoom canvas to maximum zoom factor
  - (F) : zoom canvas to fit in window ( or zoom to real size )
  
  - (D) : show/hide mouse coordinates (in units) at the bottom
  - (E) : export to PNG file

---

### CHANGES TO THE NORMAL WAY OF USING p5.js

- In `createCanvas()`,  Instead of providing `width` and `height` you have to provide an object (see example)
- `noLoop()` is the default, since the main purpose of this addon is to create static art.

---

### EXAMPLE ([see with p5 editor](https://editor.p5js.org/ElTapir/present/qaPA21W51 "p5.start2d.js boilerplate"))

```JS
function setup() {

    createCanvas({

        // array with width and height as
        //   - numbers => [297, 210]
        //   - unit strings => ['11.6929in', '21.00cm']
        // string => 'A4' (see source for possible values - A0, A1, LETTER, ANSIA, ...)
        // default: [297, 210]
        size: [297, 210],

        // orientation
        // 'portrait'  => height = biggest parameter from size
        // 'landscape' => height = smallest parameter from size
        // default: 'unchanged'
        orientation: 'portrait',

        // units to use in sketch
        // 'mm', 'cm', 'in', 'px'
        // the sizes in the size property are converted to this units
        // default: 'mm'
        units: 'mm',

        // output resolution (ie. exporting canvas to file)
        // default : 300
        ppi: 300,

        // maximum zoom
        // default : 2.0
        maxZoom: 2.0,

        // minimum zoom => can change to fit on screen
        // default : 0.1
        minZoom: 0.1,

        // zoom step size
        // default 0.025
        zoomInc: 0.025,
        
        // space between artwork and window/screen border
        // number => 32 (pixels)
        // unit string => '1.5cm' or '0.5in' or '32px'
        // 'default : '10mm'
        screenPadding: '20mm',

        // screen resolution
        // default : 96
        screenPPI: 96,         
        
        // shadow visible
        shadowVisible: true, 
        // shadow color
        shadowColor: 'rgba(64, 64, 64, 0.5)',
        // unit value (string : ex. '1cm')
        shadowX: '0mm',
        // unit value (string : ex. '10mm')
        shadowY: '6mm',
        // unit value (string : ex. '0.4in')
        shadowBlur: '10mm',
        
        // wallpaper color (body)
        // default : '#dddddd'
        wallpaperColor: '#808080',
        
        // output file name
        outputFileName: 'artwork-@date-@seed',

        // @date gives date & time
        // @seed gives current seed value
        //
        //        title    date    time  seed
        // ex. : artwork-20191231-191030-1234
        
        // number of decimals when showing mouse coordinates
        // default: 2
        xyDisplayDecimals: 2, // number of decimals for mouse cooordinates display

    });

    background(255, 128, 0);
}

function draw() {

    // PUT SOMETHING AMAZING HERE
}

```

### For a working example, see the files :
* `index.html`
* `artwork.js` or `artwork-inst.js`

---

### CONVERTING PNG TO PDF

To convert PNG files to PDF files I use `imagemagick` (cross platform : linux, mac, win, ...)

`$ convert -quality 100 -density 300 artwork.png artwork.pdf`

( the density is the resolution/ppi used in your createCanvas parameters )

---

### LICENSE

LGPL2.1, see [LICENSE.txt](LICENSE.txt) for details.
