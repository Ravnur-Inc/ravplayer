# Ravnur Media Player Documentation

This documentation provides a guide to installing, initializing, setting up, and using the Ravnur Media Player within your projects. Covering topics such as configuring playback options, handling events, and utilizing features like digital rights management (DRM) and encryption, this documentation offers instructions for integrating the Ravnur Media Player into your applications. Whether you're transitioning from legacy players like [Azure Media Player](https://learn.microsoft.com/en-us/azure/media-services/azure-media-player/azure-media-player-overview) or exploring alternatives for your project, the Ravnur Media Player offers a compatible solution.

## Get started
 
1. [Installation](#installation)
   - [Using CDN](#using-cdn)
   - [Add to Codebase](#add-to-codebase)
   - [Using private NPM registry](#using-npm-registry)

2. [Initialization](#initialization)

3. [Setup](#setup)

4. [Demo page](#demo-page)
   

## How to use

5. [Options](#options)

6. [Events](#events)

7. [Emits](#emits)

8. [Methods](#methods)

7. [Types (Flow syntax)](#types-flow-syntax)

8. [Advanced Encryption Standard (AES) example](#advanced-encryption-standard-aes-example)

9. [Digital Rights Management (DRM) examples](#digital-rights-management-drm-examples)
   - [Widevine](#widevine)
   - [Playready](#playready)
   - [Fairplay](#fairplay)

10. [Time data](#time-data-example)
      - [Closed Captions](#closed-captions)
      - [Annotations](#annotations)
      - [Chapters](#chapters)


## Get started
 Get the Ravnur Media Player up and running in your application. Follow the steps below to begin using the Ravnur Media Player in your web applications.


### Installation
___

#### Using CDN

Include the Ravnur Media Player script in your HTML file by adding the following CDN link in the `<head>` section:

```
<script src=”https://unpkg.com/ravnur-player-public@latest/dist/cdn/RavnurMediaPlayer.min.js” ></script>
```

#### Add to Codebase

Alternatively, you can include the Ravnur Media Player script to your project's codebase. Ensure that you include the script in your HTML file:

```
<script src="path/to/RavnurMediaPlayer.min.js"></script>
```

#### Using NPM registry

You can also install Ravnur Media Player using the npm registry. 

1. Install Ravnur Player

```
npm install ravnur-player-public
```

2. Include the player import in the file

```
import { RavnurMediaPlayer } from 'ravnur-player-public'
```


### Initialization
___

To use the Ravnur Media Player, initiate a new instance by providing the target element and styles:

HTML
```
<div id="player" style="max-width: 720px; height: 400px;"></div>
```
JavaScript

```
// Retrieve the HTML element where the player will be initialized
const element = document.getElementById('player');

// Define custom styling options for the player (Optional)
const styles = { ... }; // Player$Styles type

// Initialize the Ravnur Media Player instance
const player = new RavnurMediaPlayer(element, styles);
```
By following these instructions, you'll successfully initialize the Ravnur Media Player for integration into your web application.

### Setup
___

After initialization, set up the player with a media source and additional options.

```
// Define an object containing media source information. Refer to the Main Types section below for details.
let media = {
   src: 'YOUR_MEDIA_SOURCE_URL',
   type: "YOUR_MEDIA_MIME_TYPE",
}; // Player$Source type

// Object containing player options
let options = { ... };

player.setup(media, options); 
```
> [!NOTE]
 Important! Ensure to replace 'YOUR_MEDIA_SOURCE_URL' with the actual URL of your media source, and "YOUR_MEDIA_MIME_TYPE" with the appropriate MIME type of your media content.

You can use the 'destroy' method to remove a player from the DOM and destroy it.

```
player.destroy();
player = null;
```

### Demo page
___
Explore the capabilities of the Ravnur Media Player through our interactive demo pages:

### [Demo 1](https://strmsdemo.z13.web.core.windows.net/)


### [Demo 2](https://strmsdemo.z13.web.core.windows.net/html-demo/index.html)

#### Code examples
For further guidance, access our repository of code examples for popular JavaScript frameworks and vanilla JavaScript:
[here](/player-demos). These examples can be referenced and adapted to implement Ravnur Media Player within your own project.

These examples can be referenced and adapted to implement Ravnur Media Player within your project.

___


## Implementation Instructions

This part of the guide provides  instructions for integrating the Ravnur Media Player into your projects. It covers understanding and configuring options, managing events, emitting signals, and utilizing methods. By following the instructions provided below, you will be able to implement the Ravnur Media Player into your applications.

### Options


The Ravnur Media Player provides a set of options to customize the behavior and appearance of the player. Below is a list of available options, including default values and descriptions.

___

| Property | Default value | Type | Description |
| :--- | :----: | :---: | :--- |
| aesToken | `undefined` | `string` | **AES Token value**. This property specifies the AES Token used for decryption. [AES Token Example](/ravnur-player-instructions.md#advanced-encryption-standard-aes-example)). |
| logger | `null` | `Player$Logger` | Custom logger |
| loggerLevel | `2` | `number` | This parameter sets the severity of logs |
| i18n |  | `Player$Translation` | Custom translations object |
| showPlay | `true` | `boolean` | Shows play button |
| showProgress | `true` | `boolean` | Shows progress bar |
| showVolume | `true` (`false` on mobile) | `boolean` | Shows volume control |
| showFullScreen | `true` (`false` for audio) | `boolean` | Shows full screen button |
| showTheaterMode | `false` | `boolean` | Shows theater mode button |
| showClosedCaptions | `true` | `boolean` | Shows captions |
| showCaptionSearch | `false` | `boolean` | Shows captions search menu item |
| showTOC | `true` (`false` for audio) | `boolean` | Shows chapters |
| showAnnotations | `true` (`false` for audio) | `boolean` | Shows annotations |
| showQuality | `true` (`false` on mobile and for audio) | `boolean` | Shows quality levels |
| showAudioTracks | `false` | `boolean` | Shows audio tracks |
| showPoster | `true` | `boolean` | Shows poster image |
| showPlaceholder | `true` | `boolean` | Adds play button as an overlay |
| showPlaybackRate | `true` (`false` for Android) | `boolean` | Shows playback rate option in settings |
| showForward | `true` | `boolean` | Shows 10 sec forward button |
| showBackward | `true` | `boolean` | Shows 10 sec backward button |
| showSettings | `true` | `boolean` | Shows settings button |
| showDownload | `true` | `boolean` | Shows download button |
| showTitle | `true` (`false` on mobile) | `boolean` | Shows media title |
| showNextFrame | `false` | `boolean` | Shows next frame button |
| showPrevFrame | `false` | `boolean` | Shows prev frame button |
| showCCLayout | `true` (`false` on mobile) | `boolean` | Enables a caption layout option in CC settings |
| showPrev | `false` | `boolean` | Shows next track button in a full screen mode |
| showNext | `false` | `boolean` | Shows prev track button in a full screen mode |
| showCrawl | `false` | `boolean` | Shows the crawl text |
| crawl | `null` | `Player$CrawlOptions` | Crawl text configurations |
| isProgressLiveStream | `false` |`boolean` | If `true`, disables progress bar click event and current time indicator |
| showSubtitles | `false` | `boolean` | Disables captions build in the manifest |
| isAudio | `false` (`true` for audio) | `boolean` | Turns on players audio mode |
| timecode | `0` | `number` | Sets time code value |
| frameRate | `23.976` | `number` | Sets frame rate value |
| clip | `undefined` | `[number, number]` | Plays part of the media |
| autoStart | `false` | `boolean` | Enables autoplay |
| startTime | `null` | `number`| Sets media start time |
| endTime | `null` | `number` | Sets media end time |
| useNativeControls | `false` | `boolean` | Removes all the elements from the player and allows only native controls |
| useOriginTimeForPreview | `true` | `boolean` | Enables origin time frame for a preview |
| playlistmode | `auto` | `Player$PlaylistMode` | Controls a playlist position |
| plalistAutoGoNext | `true` | `boolean` | Plays the next media when the current has ended |
| playlistitle | `''` | `string` | Playlist title value |
| playlistforcepoint | `0` | `number` | Minimum width in pixels. If the player is resized to a width lower than this value, the playlist mode will be changed to 'bottom'|
| playLoop | `false` | `boolean` | Automatically starts playing from the beginning when the media has ended. |
| hideplaylist | `false` | `boolean` | Hides playlist media previews |
| showExtensions | `true` | `boolean` | Determines whether to display custom extensions, including controls like progress bar, settings, and captions |
| alwaysShowExtensions | `false` | `boolean` | Keeps showing extensions even if the media is playing |
| extensionsVisibilityTimeout | `2000` ms (`4000` ms on mobile) | `number` | Hides extensions if media is playing after this time. |
| skipDelta | `10` | `number` | Value in seconds which is used for media skip forward/backward functionality |
| keyboardListeners | `{}` | `{ [keyCode]: (player) => void }` | allows the customization of key codes and their handle functions |
| globalKeyboardListeners | `false` | `boolean` | controls whether keyboard commands are observed and acted upon across the entire webpage or within the player area. When set to true, keyboard inputs affect the entire webpage, while false restricts them to interactions within the player only |
| isHandlingKeyboardEvents | `true` | `boolean` | Enables keyboard event handling |
| bufferingTimeout | `200` | `number` | Specifies the delay in milliseconds, before displaying the processing spinner during buffering |
| isMobile | `false` (`true` on mobile devices) | `boolean` | Enables mobile mode in the player |
| hlsjsURL | `https://cdn.jsdelivr.net/ hls.js/latest/hls.min.js` | `string` | URL to specific hls.js version |
| flashPath | `/` | `string` | Path to a specific Flash version |
| savePlayTime | `false` | `boolean` | If enabled, the player will save the last watched time in the browser's local storage. This allows the player to resume playback from the saved time during the next visit. |
| widevineURL | `undefined` | `string` | Widevine license server URL. [Example](#widevine). |
| playreadyURL | `undefined` | `string` | Playready license server URL. [Example](#playready). |
| fairplayURL | `undefined` | `string` | Fairplay license server URL. [Example](#fairplay). |
| fairplayCertificateUrl | `undefined` | `string` | Fairplay license certificate URL. |
| playbackRates | `[0.5, 0.8, 1, 1.5, 2, 3, 5]` | Array of numbers | Custom playback rate options: an array of numbers from 0.01 to 5. For example, `[0.25, 0.50, 1, 1.75]`. Option 1 is always present as "Standard", and option 5 is hidden for audio-only media.|

### Events
___

You can monitor the player events using the `player.on()` method. The player also supports all HTMLMediaElement events. For details, refer to the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement).

The following table provides a description of each player event and its purpose:

| Name               | Data | Trigger Event Description                 |
|--------------------| :----: |-------------------------------------------|
| audiotrackswitched | `null` | The player changes audio tracks.          |
| handle-play-clicked| `null` | The play button is clicked.               |
| theaterchanging    | `null` | Theater mode is changed.                  |
| fullscreenchanging  | `boolean`                            | Full-screen mode changes.                                     |
| toclang             | `string`                             | Cue points language changes.                                  |
| cclang              | `string`                             | Captions language changes.                                    |
| annotationslang     | `string`                             | Annotations language changes.                                 |
| qualitychange       | `string`                             | The quality level changes.                                    |
| resizeplayer|`{ width, height, outerWidth }`| The player size changes.|
| prevtrack           | `null`                               | Switching to the previous track in the playlist.              |
| nexttrack           | `null`                               | Switching to the next track in the playlist.                  |
| mobiletouch         | `null`                               | Mobile touch events.                                          |
| downloadRequested   | `string`                             | The player returns the download URL per the user's request to download the media. |
| statechanged        | `Player$State`                       | The player state changes.                                     |
| cclayoutchange      | `{ mode, fontSize }`                 | The closed captions layout changes.                           |
| captionschange      | `Player$TimeDataSource`              | The captions change.                                          |
| changeplaylistmode  | `bottom / right`                     | The player playlist mode changes.                             |
| changesource        | `Player$Source`                      | The current media source changes.                             |




### Emits
___

Emits are designed to notify the player of specific actions or changes, allowing for dynamic updates and synchronization with external components or user interactions.
You have the option to manually trigger these events. For instance, you can use the following example: `player.bus.emit('fullscreenchanging', false);`

| Name | Payload | Description |
| :--- | :----: | :--- |
|fullscreenchanging|`boolean`|Alters full-screen mode|
|toclang|`string`|Modifies language for cue points|
|cclang|`string`|Modifies language for captions|
|annotationslang|`string`|Modifies language for annotations|
|prevtrack|`null`|Switches to the previous media in the playlist|
|nexttrack|`null`|Switches to the next media in the playlist|
|changeplaylistmode|`bottom` \| `right`|Changes the player's playlist mode|
|changesource|`Player$Source`|Changes the current media source|

### Methods
___
 The Ravnur Media Player has a set of tools to control and manipulate media playback within web applications. Customize playback controls, dynamically load media sources, select quality levels, audio tracks, and more. This provided the flexibility and control needed to create interactive media experiences. 
 
Example of usage: `player.controller.getCurrentTime();`.

| Method | Payload | Return | Description |
| :--- | :----: | :----: | :--- |
|getCurrentTime| - | `number` | Retrieves the current time of the media in seconds|
|setCurrentTime| `number` | - | Sets the player's playback time|
|isPaused| - | `boolean` | Checks if the media is currently paused|
|isEnded| - | `boolean` | Checks if the media has reached the end|
|isMuted| - | - | Checks if the player is currently muted|
|play| - | `Promise` | Initiates playback of the media. Returns a `Promise` resolved when playback begins|
|pause| - | - | Pauses the current playback|
|prevFrame| - | - | Steps to the previous frame in the media|
|nextFrame| - | - | Steps to the next frame in the media|
|getDuration| - | `number` | Retrieves the duration of the media in seconds|
|setMuted| `boolean` | - | Adjusts the muted state of the player|
|getVolume| - | `number` | Retrieves the current volume level|
|setVolume| `number` | - | Sets the volume level of the player|
|getLevels| - | Array of objects | Retrieves the available quality levels|
|getLevel| - | Object | Retrieves the current quality level|
|setLevel| Object | - | Sets the quality level of the media|
|isMultiQuality| - | `boolean` | Checks if the media has multiple quality options|
|isMultiAudioTracks| - | `boolean` | Checks if the media has multiple audio tracks|
|getAudioTracks| - | Array of objects | Retrieves the available audio tracks|
|getAudioTrack| - | `number` | Retrieves the index of the current audio track|
|setAudioTrack| `number` | - | Sets the current audio track by index|
|load| `Player$Source` | - | Loads a new media source|
|getBufferedPercent| - | `number` | Retrieves the current buffered percentage|
|getElement| - | HTML element | Retrieves the player element|
|_getFrameDuration| - | `number` | Retrieves the current frame duration|
|refreshCrawlExtension|`crawl: Player$CrawlOptions, visibility: boolean`| - |Refreshes crawl options in the player|
|setPlaybackRate|`number`| - |Sets the current playback rate|


### Types (Flow syntax)
---
Explore the type definitions in the RMPlayer codebase to understand the structure of various objects and data. This can help in understanding and maintenance of the player implementation.

####  Type Definition for a function used for Logging purposes 
```
type Player$LoggerFn = (...args: Array<mixed>) => void

type Player$Logger = {
   debug : Player$LoggerFn,
   log   : Player$LoggerFn,
   warn  : Player$LoggerFn,
   error : Player$LoggerFn
}

type Player$LoggerFn = (...args: Array<mixed>) => void


```
#### Type Definition for Crawl Options
```
type Player$CrawlOptions = {
   text: string,
   speed: number,
   backgroundColor: string,
   textColor: string
}
```
#### Type Definition for Playlist Mode
```

type Player$PlaylistMode = 'bottom' | 'right' | 'auto';
```
#### Type Definition for Source Status
```

type Player$SourceStatus = 0 | 1 | 2;

```
#### Type Definition for Time Data Source
```

type Player$TimeDataSource = {
   src: string,
   label: string,
   srclang: string,
   default?: boolean,
   type?: 'json' | 'vtt',
   state?: Player$SourceStatus
}
```
#### Type Definition for Player Source
 The `Player$Source` type is particularly important as it defines the structure of the media source object you will use during [Setup](/ravnur-player-instructions.md#setup).
```
type Player$Source = {
   id: string;
   src: string,
   type: string, // 'application/x-mpegURL', 'video/mp4' and etc.
   title: string,
   annotations?: Player$TimeDataSource[],
   chapters?: Player$TimeDataSource[],
   cc?: Player$TimeDataSource[],
   preview?: ?string,
   poster?: ?string,
   thumbnails?: ?string,
   clip?: ?[number, number] // [ 10, 300 ] sec
}
```
#### Type Definition for Closed Caption (CC) Colors
```

type Player$CCColor = '#F44336'
   | '#9C27B0' | '#3F51B5' | '#2196F3' | '#4CAF50'
   | '#FFEB3B' | '#FF9800' | '#795548' | '#9E9E9E' | '#FFF' | '#000'

```
#### Type Definition for Closed Caption (CC) Font Sizes
```

type Player$CCFontSize = '75%' | '100%' | '125%' | '150%' | '200%'

```
#### Type Definition for Closed Caption (CC) Font Families
```

type Player$CCFontFamily = '"Courier New", Courier, "Nimbus Mono L", "Cutive Mono", monospace'
   | '"Times New Roman", Times, Georgia, Cambria, "PT Serif Caption", serif'
   | '"Deja Vu Sans Mono", "Lucida Console", Monaco, Consolas, "PT Mono", monospace'
   | 'Roboto, "Arial Unicode Ms", Arial, Helvetica, Verdana, sans-serif'

```
#### Type Definition for Closed Caption (CC) Location
```

type Player$CCLocation = 'over' | 'below'

```
#### Type Definition for Closed Caption (CC) State
```

type Player$StateCC = {
   color: Player$CCColor,
   bgcolor: Player$CCColor,
   fontSize: Player$CCFontSize,
   fontFamily: Player$CCFontFamily,
   location: Player$CCLocation,
   lang: ?string,
   sources: Player$TimeDataSource[],
   loading?: boolean,
   timedata: Player$TimeData[],
   timedataLang: string
}

```
#### Type Definition for Table of Contents (TOC) State
```

type Player$StateTOC = {
   lang: ?string,
   sources: Player$TimeDataSource[],
   timedata: Player$TimeData[],
   timedataLang: string
}

```
#### Type Definition for Player State
```

type Player$State = {
   isFullScreen: boolean,
   isTheaterMode: boolean,
   cc: Player$StateCC,
   toc: Player$StateTOC
}
```
#### Type Definition for Player Styles
```

type Player$Styles = {
   accentColor: string,
   mainColor: string,
   submenuBgColor: string,
   submenuColor: string,
   chaptersBubbleColor: string,
   pltHeight: string,
   rplaylistHeight: string
}
```
#### Type Definition for Time Data
```

 type Player$TimeData = {
   id: string,
   from: number,
   to: number,
   text: string,
   title?: ?string
}
```
#### Type Definition for Player Translation
```

type Player$Translation = {
   'fullscreen': string,
   'exit-fullscreen': string,
   'theater': string,
   'exit-theater': string,
   'play': string,
   'pause': string,
   'replay': string,
   'standard-playbackrate': string,
   'forward': string,
   'backward': string,
   'prevframe': string,
   'nextframe': string,
   'annotations': string,
   'quality': string,
   'audio-track': string,
   'playback-rate': string,
   'settings': string,
   'buffering': string,
   'cc': string,
   'chapters': string,
   'back': string,
   'settings-fontcolor': string,
   'settings-fontsize': string,
   'settings-fontfamily': string,
   'settings-background': string,
   'settings-captionlocations': string,
   'help': string,
   'download': string,
   'video-only': string,
   'video-and': string,
   'language': string,
   'unapproved-source': string,
   'translate': string,
   'translating': string,
   'monoserif'  : string,
   'propserif'  : string,
   'monosans'   : string,
   'propssans'  : string,
   'cc-location-over'    : string,
   'cc-location-below'   : string,
   'red'     : string,
   'purple'  : string,
   'indigo'  : string,
   'blue'    : string,
   'green'   : string,
   'yellow'  : string,
   'orange'  : string,
   'brown'   : string,
   'grey'    : string,
   'white'   : string,
   'black'   : string,
   'help-bacward'  : string,
   'help-play'     : string,
   'help-skip'     : string,
   'help-volume'   : string,
   'help-esc'      : string,
   'no-video'      : string,
   'no-flash'      : string,
   'playlist-count-of': string
}
```

### Advanced Encryption Standard (AES) example
___

In order to enable AES encryption, you need to pass the [AES token](/ravnur-player-instructions.md#:~:text=Description-,aesToken,-undefined) along with other options before loading the source. 

> [!NOTE]
> Note that you should only pass the token value itself without any modifications such as 'Bearer'. Moreover, the AES implementation won't work on IOS devices. To make it work, you will need to implement your own proxy.
>  For additional context, you may refer to the instructions on making [Token-authorized AES-encrypted HLS streams work in Safari](https://azure.microsoft.com/fr-fr/blog/how-to-make-token-authorized-aes-encrypted-hls-stream-working-in-safari/).

```
let media = {
   src: 'YOUR_MEDIA_SOURCE',
   type: "YOUR_MEDIA_MIME_TYPE",
};

let options = {
   aesToken: 'YOUR_AES_TOKEN'
};

player.setup(media, options); 
```

> [!NOTE]
> Reminder: Ensure to replace 'YOUR_MEDIA_SOURCE_URL' with the actual URL of your media source, and "YOUR_MEDIA_MIME_TYPE" with the appropriate MIME type of your media content. See [Setup](/ravnur-player-instructions.md#setup).


### Digital Rights Management (DRM) examples
___
In the case of using RMS API, there is a separate page on [How to configure and test DRM feature](https://github.com/Ravnur-Inc/ams-api-replacement-demo-app/blob/main/docs/drm-user-guide.md).

#### Widevine 

[Learn more](https://www.widevine.com/about) about Widevine DRM technology. 

```
let media = {
   src: 'YOUR_MEDIA_SOURCE',
   type: "YOUR_MEDIA_MIME_TYPE",
};

let options = {
   widevineURL: 'YOUR_WIDEVINE_LICENSE_SERVER_URL'
};

player.setup(media, options); 
```

Make sure to update the variables with relevant information.

#### Playready 

[Learn more](https://learn.microsoft.com/en-us/playready/) about Playready DRM technology. 

```
let media = {
   src: 'YOUR_MEDIA_SOURCE',
   type: "YOUR_MEDIA_MIME_TYPE",
};

let options = {
   playreadyURL: 'YOUR_PLAYREADY_LICENSE_SERVER_URL'
};

player.setup(media, options); 
```
Make sure to update the variables with relevant information.

#### Fairplay 

[Learn more](https://developer.apple.com/streaming/fps/) about Fairplay DRM technology. 

```
let media = {
   src: 'YOUR_MEDIA_SOURCE',
   type: "YOUR_MEDIA_MIME_TYPE",
};

let options = {
   fairplayURL: 'YOUR_FAIRPLAY_LICENSE_SERVER_URL',
   fairplayCertificateUrl: 'YOUR_FAIRPLAY_LICENSE_CERTIFICATE_URL',
};

player.setup(media, options); 
```
Make sure to update the variables with relevant information.

### Time data example
___

The Ravnur Media Player lets you customize your media time data. Use chapters, annotations, and closed captions (CC) – all based on the [`Player$TimeDataSource`](#types-flow-syntax) type. Chapters break content into sections for easy navigation,  annotations let you include notes, commentary, or links at specific moments, and CC makes your content accessible with a text transcript of the audio. You can find an example [here](https://github.com/Ravnur-Inc/ams-api-replacement-demo-app/blob/main/player-demos/html-demo/app.js).

#### Closed Captions 

In the case of using RMS API, you have the option to configure ["CC generation using Video Indexer in RMS"](https://github.com/Ravnur-Inc/ams-api-replacement-demo-app/blob/main/docs/audio-analyzer-job-with-video-indexer.md).

[Example VTT file](https://github.com/Ravnur-Inc/ams-api-replacement-demo-app/blob/main/player-demos/html-demo/src/closed-captions/cc_en.vtt)

```
var closedCaptions = [
   {
      src: "/en.vtt",
      label: "English",
      kind: "captions",
      srclang: "en-us",
      default: true,
   },
   {
      src: "/ge.vtt",
      label: "German",
      kind: "captions",
      srclang: "ge",
   }
];

let media = {
   src: 'YOUR_MEDIA_SOURCE',
   type: "YOUR_MEDIA_MIME_TYPE",
   cc: closedCaptions
};

let options = {
   // Enabled by default, disabled for audio
   showClosedCaptions: true,

   // Disabled by default. Enables a cc search menu item
   showCaptionSearch: true,

   // Enabled by default, disabled for mobile devices.
   // Shows captions location option in captions settings - below the video or overlaid.
   // Default location is overlaid.
   showCCLayout: true,
};

player.setup(media, options); 
```

#### Annotations

[Example JSON file](https://github.com/Ravnur-Inc/ams-api-replacement-demo-app/blob/main/player-demos/html-demo/src/annotations/annotations.json)

```
var annotations = [
      {
        src: "/en.json",
        label: "English",
        srclang: "en-us",
      },
      {
        src: '/ge.json',
        label: 'German',
        srclang: 'ge'
      }
    ];

let media = {
   src: 'YOUR_MEDIA_SOURCE',
   type: "YOUR_MEDIA_MIME_TYPE",
   annotations: annotations
};

let options = {
   showAnnotations: true, // Enabled by default, disabled for audio
};

player.setup(media, options); 
```

#### Chapters

[Example VTT file](https://github.com/Ravnur-Inc/ams-api-replacement-demo-app/blob/main/player-demos/html-demo/src/chapters/chapters_en.vtt)

```
var chapters = [
  {
    src: "/en.vtt",
    label: "English",
    srclang: "en-us",
    default: true,
  },
  {
    src: "/ge.vtt",
    label: "German",
    srclang: "ge"
  },
];

let media = {
   src: 'YOUR_MEDIA_SOURCE',
   type: "YOUR_MEDIA_MIME_TYPE",
   chapters: chapters
};

let options = {
   showTOC: true, // Enabled by default, disabled for audio
};

player.setup(media, options); 
```

___

Congratulations on completing the integration of Ravnur Media Player into your project! Should you encounter any issues or have questions during the implementation process, don't hesitate to reach out to our technical support team for assistance. We're here to help ensure a successful integration of the Ravnur Media Player into your applications.
