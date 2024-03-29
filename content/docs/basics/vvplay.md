---
title: "Command vvplay"
description: ""
summary: ""
date: 2024-03-29T16:28:07+08:00
lastmod: 2024-03-29T16:28:07+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "vvplay-1711700887"
    weight: 20
toc: true
seo:
  title: ""
  description: ""
  canonical: ""
  noindex: false
---
## `vvplay`

Plays a folder of pcd/ply/bin files in lexicographical order. A window will appear upon running the binary from which you can navigate using your mouse and keyboard. Controls are described further below.

```shell
Plays a folder of point cloud files in lexicographical order

Usage: vvplay [OPTIONS] <SRC>

Arguments:
  <SRC>  src can be: 1. Directory with all the pcd files in lexicographical order 2. location of the mpd file

Options:
  -q, --quality <QUALITY>            [default: 0]
  -f, --fps <FPS>                    [default: 30]
  -x, --camera-x <CAMERA_X>          [default: 0]
  -y, --camera-y <CAMERA_Y>          [default: 0]
  -z, --camera-z <CAMERA_Z>          [default: 1.3]
      --yaw <CAMERA_YAW>             [default: -90]
      --pitch <CAMERA_PITCH>         [default: 0]
  -W, --width <WIDTH>                [default: 1600]
  -H, --height <HEIGHT>              [default: 900]
      --controls
  -b, --buffer-size <BUFFER_SIZE>
  -m, --metrics <METRICS>
      --decoder <DECODER_TYPE>       [default: noop] [possible values: noop, draco]
      --decoder-path <DECODER_PATH>
      --bg-color <BG_COLOR>          [default: rgb(255,255,255)]
  -h, --help                         Print help
```

### Controls

With the main screen focused,

1. `W` Key - Moves your position to the front
2. `A` Key - Moves your position to the left
3. `S` Key - Moves your position to the back
4. `D` Key - Moves your position to the right
5. `Q` Key - Moves your position up
6. `E` Key - Moves your position down
7. `0` Key - Resets your position to the initial position
8. `Space` Key - Toggles Play/Pause
9. `LeftArrow` Key - Rewinds by 1 frame
10. `RightArrow` Key - Advances by 1 frame
11. `Mouse` Drag - Adjusts camera yaw / pitch (Hold right click on Mac, left click on Windows)
12. `L` Key - Rotates camera horizontally(around the Y axis) clockwise
13. `J` Key - Rotates camera horizontally(around the Y axis) counterclockwise
14. `I` Key - Rotates camera vertically(around the X axis) clockwise
15. `K` Key - Rotates camera vertically(around the X axis) counterclockwise
16. Adjusts camera yaw/picth with mouse (Hold right click on Mac, left click on Windows)

With the secondary window focused,

![Playback Controls Secondary Window](https://raw.githubusercontent.com/nus-vv-streams/vvtk/main/docs/images/playback_controls.png)

The Play/Pause button toggles between play and pause. The slider allows you to navigate to any frame you wish.

The information displayed in the window are:

1. Current Frame / Total Frames
2. Camera Information - Useful to recreate a certain view through command line arguments

### Example

The following command will play all `.pcd` files in the `./pcds/` directory.

```shell
vvplay ./pcds
```

You can buffer the render with a set number of frames using `-b`

```shell
vvplay ./pcds -b 100
```

You can specify the background color using `--bg-color` in the following two ways.

1. use rgb value: rgb(r,g,b)
2. use hex rgb number: #RRGGBB

```shell
vvplay ./pcds --bg-color "#9ef244"
vvplay ./pcds --bg-color "rgb(10,23,189)"
```
