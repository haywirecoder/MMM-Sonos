# MMM-Sonos

<p>
<a href="https://github.com/jishi/node-sonos-http-api"><img src="https://img.shields.io/badge/Sonos-API-orange.svg" alt="API"></a>
<a href="http://choosealicense.com/licenses/mit"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License"></a>
</p>

This is an adaption and modification of of [Vaggan's](https://github.com/Vaggan) [MagicMirror-SonosModule](https://github.com/Vaggan/MagicMirror-SonosModule) and [CFenner's](https://github.com/CFenner) [MagicMirror-SonosModule](https://github.com/CFenner/MagicMirror-Sonos-Module). It was modified to get some enhancements in visualisation an configuration. Also the module hides itself when not playing now.

Note from Snille: I'm new to the MagicMirror world and Node.js, this is my first attempt to modify a module. There are probably lot's of things that could have been done better. :)

When starting the Mirror:

![Sonos Module Loading](https://github.com/haywirecoder/MMM-Sonos/blob/master/.github/Sonos-Loading.png)

Module on the Left side of the Mirror:

![Sonos Module Left](https://github.com/haywirecoder/MMM-Sonos/blob/master/.github/sonos.png)


## Usage

_Prerequisites_

- requires MagicMirror v2.0.0
- install and [run](https://github.com/MichMich/MagicMirror/wiki/Auto-Starting-MagicMirror) [node-sonos-http-api](https://github.com/jishi/node-sonos-http-api)

### Installation

In your terminal, go to your MagicMirror's Module folder:

```
cd ~/MagicMirror/modules
```

Clone this repository:

```
git clone https://github.com/haywirecoder/MMM-Sonos.git
```

Add some [config entries](#configuration) to your config.js file. After that the content will be added to your mirror.

### Configuration

To run the module properly, you need to add the following data to your config.js file.

```
{
	module: 'MMM-Sonos',
	header: "Playing on SONOS",
	position: "top_center", // This can be any of the regions, best results in center regions
	classes: "default everyone",
	config: {
		// See 'Configuration options' for more information.
	}
}
```

Here are the configuration options to configure the module.

| Option | Description |
|---|---| 
|`showStoppedRoom`|Trigger the visualization of stopped rooms.<br><br>**Default value:** `true`|
|`showAlbumArt`|Trigger the visualization of the album art.<br><br>**Default value:** `true`|
|`showRoomName`|Trigger the visualization of the room name.<br><br>**Default value:** `true`|
|`preRoomText`|Text to be displayed before the zone name.<br><br>**Default value:** `Zone: `|
|`preArtistText`|Text to be displayed before the artist name.<br><br>**Default value:** `Artist: `|
|`preTrackText`|Text to be displayed before the track name.<br><br>**Default value:** `Track: `|
|`preTypeText`|Text to be displayed before the source name.<br><br>**Default value:** `Source: `|
|`animationSpeed`|Lenght of the fade animation.<br><br>**Default value:** `1000`|
|`updateInterval`|Update interval.<br><br>**Default value:** `0.5`|
|`apiBase`|http link to the SONOS API.<br><br>**Default value:** `http://localhost'`|
|`apiPort`|SONOS API port.<br><br>**Default value:** `5005`|
|`apiEndpoint`|Link to the "zones" information on the SONOS API.<br><br>**Default value:** `zones`|
|`exclude`|Zones names to exclude ["Secret-Room","Greenhouse"].<br><br>**Default value:** `[]`|



### Known Issues

The module may not be able to access the data of the sonos API due to a Cross-Origin Resource Sharing (CORS) issue. This could be solved by adding the following lines to the `sonos-http-api.js` just before `res.write(new Buffer(jsonResponse));` in the sonos api. Remember to restart the service after the change.

```
  res.setHeader("Access-Control-Allow-Origin", "http://localhost");
  res.setHeader("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
```
