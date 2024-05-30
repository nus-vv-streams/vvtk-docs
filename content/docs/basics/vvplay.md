---
title: "vvplay"
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
# `vvplay`

`vvplay` is a command line volumetric video player that plays a folder of point cloud files in lexicographical order. It is a command line tool that can be used to visualize point cloud data in the form of `.pcd`, `.ply`, or `.bin` files.  The point cloud data format and directory structure is described in the [Data Format](#data-format) section.  You can navigate using your mouse and keyboard. Controls are described further below in the [GUI Controls](#controls) section.

## Command Line Arguments

You can run `vvplay` with the following:

```shell
vvplay [OPTIONS] <SRC>
```

The argument `<SRC>` is mandatory and can be one of the following:    
- a directory containing a sequence of point cloud
- a single point cloud file
- an MPD file (coming soon)
- a VPCC-encoded video file (coming soon)


### Synopsis

The following options are available.  

short option | long option | description | default
-------------|-------------|-------------|--------
  `-f` | `--fps <FPS>`     | Playback frame rate | 30 
  `-x` | `--camera-x <CAMERA_X>` | x-coordinate of the camera | 0 
  `-y` | `--camera-y <CAMERA_Y>` | y-coordinate of the camera | 0 
  `-z` | `--camera-z <CAMERA_Z>` | z-coordinate of the camera | 1.3 
  &nbsp;    | `--yaw <CAMERA_YAW>`    | Yaw of the camera (in degree) | -90
  &nbsp;    | `--pitch <CAMERA_PITCH>` | Pitch of the camera (in degree) | 0
  `-W` | `--width <WIDTH>`        | Width of the window | 1600
  `-H` | `--height <HEIGHT>`      | Height of the window | 900
  &nbsp;   | `--hide-control-panel`   | Hide control panel | false
  &nbsp;    | `--bg-color <BG_COLOR>` | Background color | rgb(255,255,255)
  `-m` | `--metrics <METRICS>`   | Metrics | 
  `-b` | `--buffer-size <BUFFER_SIZE>` | Buffer size | 0
  &nbsp;    | `--decoder <DECODER_TYPE>` | Decoder type | noop
  &nbsp;    | `--decoder-path <DECODER_PATH>` | Decoder path | 
  `-q` | `--quality <QUALITY>`  | ?? |   0
  &nbsp;    | `--adaptive-upsampling <BOOL> | Background color | false
  `-h` | `--help` | Print help |

`-f`, `--fps <FPS>`
: Specify the maximum playback frame rate of the player as a floating point number.  The default value is 30.  If the point cloud is too complex or the playback is IO-bound, the actual frame rate may be lower than the specified value.

`-x`, `--camera-x <CAMERA_X>` 
`-y`, `--camera-y <CAMERA_Y>`
`-z`, `--camera-z <CAMERA_Z>`
: Specify the x, y, and z coodinates, as floating point numbers, of the initial position of the camera. The default value is (0, 0, 1.3).

`--yaw <CAMERA_YAW>` 
`--pitch <CAMERA_PITCH>`
: Specify the yaw and pitch of the camera as two floating point numbers, in degrees. The default values are -90 and 0, respectively.

`-W`, `--width <WIDTH>`
`-H`, `--height <HEIGHT>`
: Specify the width and height of the window in pixels. The default values are 1600 and 900, respectively.

`--hide-control-panel`
: Hide the control panel for keyboard-only control. 

`--bg-color <COLOR>`
: Specify the background color of the window in sRGB space.  The color can be specified in either hex format (`#RRGGBB`) or rgb format `rgb(r,g,b)`. The default value is `rgb(255,255,255)`.

`--metrics <DIRECTORY>`
: Specify the directory that contains the quality metrics data.  The directory should contain one file, in CSV format, for each frame, in lexographical order.  Each CSV should have two columns, the name of the quality metric and the value of the quality metric.  The quality metrics information will be overlaid on the lower left corner of the window.  You can create this directory using the `vv metrics` command.

## Controls

With the main screen focused,

Key       | Action
----------|-------
`W`       | Moves your position to the front
`A`       | Moves your position to the left
`S`       | Moves your position to the back
`D`       | Moves your position to the right
`Q`       | Moves your position up
`E`       | Moves your position down
`0`       | Resets your position to the initial position
`L`       | Rotates camera horizontally(around the Y axis) clockwise
`J`       | Rotates camera horizontally(around the Y axis) counterclockwise
`I`       | Rotates camera vertically(around the X axis) clockwise
`K`       | Rotates camera vertically(around the X axis) counterclockwise
`Space`   | Toggles Play/Pause
`Left Arrow` | Rewinds by 1 frame
`Right Arrow` | Advances by 1 frame
`Escape` | Quits

Clicking and dragging (right click on Mac, left click on Windows) adjusts the camera yaw / pitch.

With the secondary window focused,

![Playback Controls Secondary Window](https://raw.githubusercontent.com/nus-vv-streams/vvtk/main/docs/images/playback_controls.png)

The Play/Pause button toggles between play and pause. The slider allows you to navigate to any frame you wish.

The information displayed in the window are:

1. Current Frame / Total Frames
2. Camera Information - Useful to recreate a certain view through command line arguments

## Example

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
