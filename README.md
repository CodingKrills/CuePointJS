# CuePointJS
HTML5 video cue point creator.

## See it in action
http://iamjohnbrown.com/cuepoint.php

## Use
**1. Add an HTML5 video element to your page.**
```
<video id="myVideo">
  <source src="video.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```

**2. Add an empty block element to your page. This will hold the dynamically created cue cards.**
``` 
<div id="cueCards"></div>
```

**3. Add jQuery and CuePointJS in the head of your page.**
```
<head>
  <script src="https://code.jquery.com/jquery-2.1.3.min.js"></script>
  <script src="cuePoint.js"></script>
</head>
```

**4. Call cuePoint(card_container, options) on the video element.**
```
var options = [
  points : [
    {
      time : "00:16",
      text : "Opening sequence."
    },
    {
      time : "03:14",
      text : "Some other descriptive caption.",
      playback : "pause"
    }
  ],
  
  hover : "hover",
  active : "active",
  inactive : "inactive"
  
];

$ (function () {
  $("#myVideo").cuePoint ("#cueCards", options);
});
```

**Card Container**
- An empty block element that will hold dynamically created cue cards.

**Options**
- points : **(object[ ])**
  - time : **(string)** The time at which to add a cue point.
  - text : **(string)** The descriptive caption.
  - playback : **(optional string) ["pause" / "play" (Default)]** Play or pause video on click.
  
- hover : **(string)** Class to use when hovering over cue cards.
- active : **(string)** Class to use for all cue points that lie before the current video time.
- inactive : **(string)** Class to use for all cue points that lie after the current video time.

## Styling
Cue points will be dynamically created as divs and appended to your card container. To style these simply add styling to the card container children.
```
#cueCards div {border:1px solid #333; border-radius:3px; padding:15px;}
````

## Quirks
To prevent your hover styling from being overridden by other styles:
- Place your hover style **after** the active and inactive styles.
```
.active { color:red; }
.inactive { color:#333; }
.hover { color:green; }
```
- Or add **!important** after your hover values.
```
.hover { color:green !important;  }
```
