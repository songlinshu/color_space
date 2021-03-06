A Rust library for converting between color spaces and comparing colors, ported from https://github.com/berendeanicolae/ColorSpace.

## Color Conversion
You can convert between any supported color spaces using the `from` trait method:
```rust
use color_space::{Rgb, Hsv};

let rgb = Rgb::new(0.0, 255.0, 0.0);
let hsv = Hsv::from(rgb);
assert_eq!(hsv, Hsv::new(120.0, 1.0, 1.0));
```

You can also do this generically with the `from_color` method:
```rust
use color_space::{Rgb, Hsv, FromColor};

let rgb = Rgb::new(0.0, 0.0, 255.0);
let hsv = Hsv::from_color(&rgb);
assert_eq!(hsv, Hsv::new(240.0, 1.0, 1.0));
```

## Comparing Colors
You can compare colors by using the `compare_*` methods:
```rust
use color_space::{Rgb, Hsv, CompareCie2000};

let rgb = Rgb::new(255.0, 0.0, 0.0);
let hsv = Hsv::new(0.0, 1.0, 1.0);
let diff = rgb.compare_cie2000(&hsv);
assert_eq!(diff, 0.0);
// these two colors are the same, so the difference is zero
```

## Currently Supported Color Spaces
* CMY
* CMYK
* HSL
* HSB
* HSV
* CIE L*AB
* Hunter LAB
* LCH
* LUV
* RGB
* XYZ
* YXY

## Currently Supported Comparisons
* Euclidean
* CIE1976
* CIE2000
* CMC

## Contibutions
I'm happy to take feedback and improvements on the API if there's ways it can be improved. I need to write more tests to check the quality of the conversion outputs as well, but they are tedious to write so I'm currently procrastinating on that.