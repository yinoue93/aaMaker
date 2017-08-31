# Ascii Art Maker

Converts real life media (images, videos) to ascii art (AA) media.

## Examples
### Images

<img src="imgs/fuji2.png" width="300"><img src="imgs/fuji2_aa.png" width="600">
<img src="imgs/img_000097.png" width="300"><img src="imgs/img_000097_aa.png" width="600">
<img src="imgs/img_000642.png" width="300"><img src="imgs/img_000642_aa.png" width="600">
<img src="imgs/img_001587.png" width="300"><img src="imgs/img_001587_aa.png" width="600">
<img src="imgs/img_001723.png" width="300"><img src="imgs/img_001723_aa.png" width="600">
<img src="imgs/img_002851.png" width="300"><img src="imgs/img_002851_aa.png" width="600">

### Videos

## Mechanics

### 1. Convert the original image to line drawing
Uses cv2.Canny(). In the below image, the white pixels indicate the edges.

<img src="imgs/fuji2.png" width="400"><img src="imgs/fuji2_line.png" width="400">
<img src="imgs/img_001723.png" width="400"><img src="imgs/img_001723_line.png" width="400">


### 2. Convert the line drawing to ascii art
The script scans through the line drawing to determine which letter is the best match. If the scanning area contains edges, then choose the best match from the list of outline characters (listed below). If else, choose the best match from the brightness characters (also listed below).　For the outline, the 'best match' is determined by the maximum convolution value between the letter and the line image for that region. For the brightness, the 'best match' is determined by the grayscale brightness value of the original image.

Outline characters:
`－=7/／ノ丿ﾉ(〈{})〉>ｊゝ1|＼<ヽへL┌」v^`

Brightness characters:
`.:;+%$%#@?012345678abcdefghijklmnopqrstuvwxyABCDEFGHIJKLMNOPQRSTUVWXYあぃいぅうぇえぉおかがきぎ くぐけげこごさざしじすずせぜそぞただちぢっつづてでとどなにぬねのはばぱひびぴふぶぷへべぺほぼぽまみむめもゃやゅゆょよらりるれろゎわゐゑをアィイゥウェエォオカガキギクグケゲコゴサザシジスズセゼソゾタダチヂッツヅテデトドナニヌネノハバパヒビピフブプヘベペホボポマミムメモャヤュユョヨラリルレロヮワヰヱヲ鬱鑑驚親軽心口斎恋麓靏`

### Convolution Examples:

### Original Image
<img src="imgs/sword.jpg" width="300">
### `－`
<img src="imgs/conv_hyphen.png" width="300">
### `|`
<img src="imgs/conv_bar.png" width="300">
### `＼`
<img src="imgs/conv_bslash.png" width="300">
### `／`
<img src="imgs/conv_fslash.png" width="300">

## Usage
usage: aaMaker.py [-h] -m SCRIPTMODE [-o AASIZE] [-b LETTERBRIGHTNESSTHRESH] [-s FONTSIZE] [-l ONLYOUTLINE] [-d DEMO] [-i IMGNAME] [-f FOLDERNAME]

aaMaker.py [Args] [Options] Detailed options -h or --help

```
optional arguments:
-h, --help
    show this help message and exit
-m SCRIPTMODE, --scriptMode SCRIPTMODE
    Script execution mode. 'img', 'live', 'letters', 'video', 'test'
-o AASIZE, --outputSize AASIZE
    Output width size
-b LETTERBRIGHTNESSTHRESH, --brigheness LETTERBRIGHTNESSTHRESH
    Brightness threshold value. Pixels under this value are set to blank (white)
-s FONTSIZE, --fontSize FONTSIZE
    Font size. Minimum is 24.
-l ONLYOUTLINE, --outlineOnly ONLYOUTLINE
    True for the output containing the outline only
-d DEMO, --demo DEMO
    Used only by "img" script mode. True to preview the   output in a window. False to save the output to a file.
-i IMGNAME, --imgname IMGNAME
    Used only by "img" script mode. The input image filename.
-f FOLDERNAME, --foldername FOLDERNAME
    Used only by "video" script mode. Foldername where the movie file is stored.
```

## Packages used
Celery
Cython
Numpy
OpenCV
