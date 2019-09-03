# Module: Plex Favorites Slideshow

Show a slideshow of images in the background. Great for a photo frame from instead of a mirror, using photos marked as 'favorite' from your PLEX Server.

The `MMM-PlexSlideshow` module is designed to display images fullscreen, one at a time on a fixed interval, from your PLEX server. These images can be shown in order or at random. The images can transition from one to the other and be shown with no edge (cover) or the enter image(contain).

Based on <a href="https://github.com/AdamMoses-GitHub/MMM-ImageSlideshow/blob/master/MMM-ImageSlideshow.js">MMM-ImageSlideshow</a>.

<img src="https://github.com/darickc/MMM-BackgroundSlideshow/blob/master/screenshots/landscape.jpg" style="width: 300px;" />
<img src="https://github.com/darickc/MMM-BackgroundSlideshow/blob/master/screenshots/portait.jpg" style="width: 300px;" />

## Dependencies / Requirements

This module requires that you have an accessable PLEX media server where your photos are stored, and that you have marked some of these photoes as favourites (The Heart icon).

## Operation

This module will take in a list of directory paths, one or more, containing image files. The module will display those images in either alphabetical or random order, across either each path one at time or across all the paths at once. Once all the images have been shown, it will loop back and start again.

Extra configurations include setting the amount of time an image is shown for, selecting which file extensions are valid, the transition speed from one image to another, the background sizing, whether or not to animate the transition from one to the other, the gradient used to make the text more readable, and the gradient opacity.

## Installing the module

To install this module, from a SSH terminal

```
cd ~/MagicMirror/modules
git clone https://github.com/PJTewkesbury/MMM-PlexSlideshow.git
cd MMM-PlexSlideshow
npm install
```

To update

```
cd ~/MagicMirror/modules/MMM-PlexSlideShow
git pull
npm install
```

## Configuration

To configure the module, add the module to the modules array in the `config/config.js` file:

```javascript
modules: [
  {
    module: 'MMM-PlexSlideshow',
	position: 'fullscreen_below',
    config: {
	  plex: {
		  hostname:"PlexServerName Or IP",
		  port:32400,
		  username:"",
		  password:"",
		},
		transitionImages: true,
    }
  }
];
```

## Notification options

The following notifications can be used:

<table width="100%">
	<!-- why, markdown... -->
	<thead>
		<tr>
			<th>Notification</th>
			<th width="100%">Description</th>
		</tr>
	<thead>
	<tbody>
		<tr>
			<td><code>BACKGROUNDSLIDESHOW_NEXT</code></td>
			<td>Change to the next image, restart the timer for image changes only if already running<br>
			</td>
		</tr>
		<tr>
			<td><code>BACKGROUNDSLIDESHOW_PAUSE</code></td>
			<td>Pause the timer for image changes<br>
			</td>
		</tr>
		<tr>
			<td><code>BACKGROUNDSLIDESHOW_PLAY</code></td>
			<td>Change to the next image and start the timer for image changes<br>
			</td>
		</tr>
</table>


## Configuration options

The following properties can be configured:

<table width="100%">
	<!-- why, markdown... -->
	<thead>
		<tr>
			<th>Option</th>
			<th width="100%">Description</th>
		</tr>
	<thead>
	<tbody>
	<tr>
			<td><code>plex</code></td>
			<td>plex connection settings<br>
				<br>This value is <b>required</b>
			</td>
		</tr>

		<tr>
			<td><code>slideshowSpeed</code></td>
			<td>Integer value, the length of time to show one image before switching to the next, in milliseconds.<br>
				<br><b>Example:</b> <code>6000</code> for 6 seconds
				<br><b>Default value:</b> <code>10000</code> or 10 seconds
				<br>This value is <b>OPTIONAL</b>
			</td>
		</tr>

    <tr>
			<td><code>transitionSpeed</code></td>
			<td>Transition speed from one image to the other, transitionImages must be true. Must be a valid css transition duration.<br>
				<br><b>Example:</b> <code>'2s'</code>
				<br><b>Default value:</b> <code>'1s'</code>
				<br>This value is <b>OPTIONAL</b>
			</td>
		</tr>
    <tr>
			<td><code>backgroundSize</code></td>
			<td>The sizing of the background image. Values can be:<br>
        cover: Resize the background image to cover the entire container, even if it has to stretch the image or cut a little bit off one of the edges.<br>
        contain: Resize the background image to make sure the image is fully visible<br>
				<br><b>Example:</b> <code>'contain'</code>
				<br><b>Default value:</b> <code>'cover'</code>
				<br>This value is <b>OPTIONAL</b>
			</td>
		</tr>
    <tr>
			<td><code>transitionImages</code></td>
			<td>Transition from one image to the other (may be a bit choppy on slower devices, or if the images are too big).<br>
				<br><b>Example:</b> <code>true</code>
				<br><b>Default value:</b> <code>false</code>
				<br>This value is <b>OPTIONAL</b>
			</td>
		</tr>
    <tr>
			<td><code>gradient</code></td>
			<td>The vertical gradient to make the text more visible.  Enter gradient stops as an array.<br>
				<br><b>Example:</b> <code>[
      "rgba(0, 0, 0, 0.75) 0%",
      "rgba(0, 0, 0, 0) 40%"
    ]</code>
				<br><b>Default value:</b> <code>[
      "rgba(0, 0, 0, 0.75) 0%",
      "rgba(0, 0, 0, 0) 40%",
      "rgba(0, 0, 0, 0) 80%",
      "rgba(0, 0, 0, 0.75) 100%"
    ]</code>
				<br>This value is <b>OPTIONAL</b>
			</td>
		</tr>
		<tr>
			<td><code>horizontalGradient</code></td>
			<td>The horizontal gradient to make the text more visible.  Enter gradient stops as an array.<br>
				<br><b>Example:</b> <code>[
      "rgba(0, 0, 0, 0.75) 0%",
      "rgba(0, 0, 0, 0) 40%"
    ]</code>
				<br><b>Default value:</b> <code>[
      "rgba(0, 0, 0, 0.75) 0%",
      "rgba(0, 0, 0, 0) 40%",
      "rgba(0, 0, 0, 0) 80%",
      "rgba(0, 0, 0, 0.75) 100%"
    ]</code>
				<br>This value is <b>OPTIONAL</b>
			</td>
		</tr>
    <tr>
			<td><code>gradientDirection</code></td>
			<td>The direction of the gradient<br>
				<br><b>Example:</b> <code>'horizontal'</code>
				<br><b>Default value:</b> <code>'vertical'</code>
				<br><b>Possible values:</b> <code>'vertical', 'horizontal', 'both'</code>
				<br>This value is <b>OPTIONAL</b>
			</td>
		</tr>
    </tbody>
</table>
