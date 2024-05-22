# Ravnur Media Player

RMS presents a Ravnur Media Player - a web-based media player that can stream adaptive bitrate video and audio. It uses the open web standards MediaSource Extensions and Encrypted Media Extensions. 

As mentioned by [Microsoft documentation](https://learn.microsoft.com/en-us/azure/media-services/azure-media-player/azure-media-player-overview), Azure Media Player only supports media streams from Azure Media Services. As an alternative, RMS recommends a Ravnur Media Player.

### Get started

The installation procedure is described in the Documentation guide. 
In general, you will just need:
1. Include the Ravnur Media Player in your project by either adding the CDN link in the <head> section of your HTML file or by installing it via npm and importing it into your project file.
2. Initiate a new instance by providing the target element and styles.
3. Set up the player with a media source and additional options.

All the code samples are included in the full guide together with player demos and implementation insights.

### Implementation possibilities

The customization capabilities allow the developer to configure options, manage events, emit signals, and utilize methods.
Here is a general list of what is offered:

| Capability (Entity)              | Description                                                                                                                                                   |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Options                          | Customize the behavior and appearance of the player.                                                                                                           |
| Events                           | Monitor the player events. The player also supports all HTMLMediaElement events.                                                                               |
| Emits                            | Notify the player of specific actions or changes, allowing for dynamic updates and synchronization with external components or user interactions. You have the option to manually trigger these events. |
| Methods                          | A set of tools to control and manipulate media playback within web applications. Customize playback controls, dynamically load media sources, select quality levels, audio tracks, and more. This provides the flexibility and control needed to create interactive media experiences. |
| Types (Flow syntax)              | Explore the type definitions in the RMPlayer codebase to understand the structure of various objects and data. This can help in understanding and maintenance of the player implementation. |
| Advanced Encryption Standard (AES) | Allows secure streaming by encrypting the media content. A custom proxy solution for compatibility is required.                                                |
| Digital Rights Management (DRM)  | Ensure secure streaming of protected media content. DRM functionality can be configured by specifying the appropriate license server URLs in the player options. We offer configuration examples for Widevine, Playready, and Fairplay. |
| Chapters                         | Customize your media with chapters, which break content into sections for easy navigation. This allows users to quickly jump to different parts of the media.   |
| Annotations                      | Add annotations to your media, enabling you to include notes, commentary, or links at specific moments.                                                         |
| Closed Captions (CC)             | Implement closed captions (CC) to make your content accessible with a text transcript of the audio.                                                            |
