# Carousely.js
A tool for building video carousels.

## How does it work?
Based on the data you give, carousely.js will create slides with three components: `Title, Video, and Description.`

### Set Up:

##### 1) Include `carousely.js` and `jQuery` in your project
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<script type="text/javascript" src="./carousely.js"></script>
```

##### 2) Add two lines of HTML to your page where you want the video carousel

```html
<div class="vid-container"></div>
<div class="dots"></div>
```

##### 3) Create an object for your content data

The object should contain three _even_ arrays and one number, setting the number of times the slideshow sould play.

```javascript

const content = {
  copy:  [
    'Video description 1',
    'Video description 2',
  ],
  title: [
    'title 1',
    'title 2',
  ],
  links: [
    'http://vjs.zencdn.net/v/oceans.mp4',
    'http://vjs.zencdn.net/v/oceans.mp4',
  ],
  repeatNumber: 3
  
}
```
> `Each array must have the same length for the slides to work`

##### 4) Import the source doe from the library and call the `playSLideShow` method to build and play the carousel

```javascript
var carousely = require('./carousely.js')
carousely.playCarousel()
```

##### 5) If you wish to style a specific slide or add logic / behavior to a specific video object, you can hook into any slide or video node with the naming conventions used in the slide rendering functions.

>  Class names for slide have a prefix of .slide- and a suffix of [number]
>  together each slide can be targeted by .slide-[number]
> Each slide shares the base class of .slide so you can hook into every slide instance using .slide

```css
/* all slides */
.slide {
  targets all slides
}

/* individual slides */
.slide-0 {
  your styles here
}
```

>  IDs for each video object share the prefix of #my_video_ and the suffix of [number]
>  together, each vide can be targeted by #my_video_[number]

```css
/* all videos */
#vid {
  targets all video instances
}

/* individual slides */
 #my_video_0 {
  your styles here
}
```

##### 6) Open the HTML file in your browser. Inspect the video and dot containers to find that Carousely has generated the following HTML for the video container.

```html
<div class="vid-container" style="display: flex;">
  <div class="slide-0 slide" data-slide="0" style="display: block;">
    <video id="my_video_0" data-video="0" src="http://vjs.zencdn.net/v/oceans.mp4" style="display: block;"></video>
    <div class="text-content-0">
      <h3 class="video-title">title ispsum dolor 1</h3>
      <p class="video-description">lorem ispsum dolor 1</p>
    </div>
  </div>
  <div class="slide-1 slide" style="display: none;">
    <video id="my_video_1" data-video="1" src="http://vjs.zencdn.net/v/oceans.mp4" controls="" preload="auto" class="vid" style="display: flex;"></video>
    <div class="text-content-1">
      <h3 class="video-title">title ispsum dolor 2</h3>
      <p class="video-description">lorem ispsum dolor 2</p>
    </div>
  </div>
  <div class="slide-2 slide" style="display: none;">
    <video id="my_video_2" data-video="2" src="http://vjs.zencdn.net/v/oceans.mp4" controls="" preload="auto" class="vid" style="display: flex;"></video>
    <div class="text-content-2">
      <h3 class="video-title">title ispsum dolor 3</h3>
      <p class="video-description">lorem ispsum dolor 3</p>
    </div>
  </div>  
</div>
```
##### 7) As well as the following output for the dot container

```html
<div class="dots">
  <div class="dot-0 dot" data-dot="0">•</div>
  <div class="dot-1 dot" data-dot="1">•</div>
  <div class="dot-2 dot" data-dot="2">•</div>
</div>
```

#### known bugs

- data object not good in that each array should contain a slide's
content, not one slide pulling form 3 arrays
