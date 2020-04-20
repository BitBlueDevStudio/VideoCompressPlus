# video_compress
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-3-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

Compress videos, remove audio, manipulate thumbnails, and make your video compatible with all platforms through this lightweight and efficient library.
100% native code was used, we do not use FFMPEG as it is very slow, bloated and the GNU license is an obstacle for commercial applications.
In addition, google chrome uses VP8/VP9, safari uses h264, and most of the time, it is necessary to encode the video in two formats, but not with this library.
All video files are encoded in an MP4 container with AAC audio that allows 100% compatibility with safari, mozila, chrome, android and iOS.

Works on ANDROID and IOS.

### How to use

## Video compression

```dart
MediaInfo mediaInfo = await VideoCompress.compressVideo(
  path,
  quality: VideoQuality.DefaultQuality, 
  deleteOrigin: false, // It's false by default
);
```

## Check compress state
```dart
VideoQuality.isCompressing
```
<!-- ## Cancel compression
```dart
await videoCompress.cancelCompression()
``` -->

## Get memory thumbnail from VideoPath
```dart
final uint8list = await VideoCompress.getByteThumbnail(
  videopath,
  quality: 50, // default(100)
  position: -1 // default(-1)
);
```

## Get File thumbnail from VideoPath
```dart
final thumbnailFile = await VideoCompress.getFileThumbnail(
  videopath,
  quality: 50, // default(100)
  position: -1 // default(-1)
);
```

## Get media information

```dart
final info = await VideoCompress.getMediaInfo(videopath);

```

## delete all cache files
- Delete all files generated by this will delete all files located at 'video_compress', you shoule ought to know what are you doing.

```dart
await VideoCompress.deleteAllCache()
```

## Listen the compression progress
```dart
class _Compress extends State<Compress> {

  Subscription _subscription;

  @override
  void initState() {
    super.initState();
    _subscription =
        VideoCompress.compressProgress$.subscribe((progress) {
      debugPrint('progress: $progress');
    });
  }

  @override
  void dispose() {
    super.dispose();
    _subscription.unsubscribe();
  }
}
```

### TODO
- Add the trim video function
- Add cancel function to Android

## Methods
|Functions|Parameters|Description|Returns|
|--|--|--|--|
|getByteThumbnail|String `path`[video path], int `quality`(1-100)[thumbnail quality], int `position`[Get a thumbnail from video position]|get thumbnail from video `path`|`Future<Uint8List>`|
|getFileThumbnail|String `path`[video path], int `quality`(1-100)[thumbnail quality], int `position`[Get a thumbnail from video position]|get thumbnail file from video `path`|`Future<File>`|
|getMediaInfo|String `path`[video path]|get media information from video `path`|`Future<MediaInfo>`|
|compressVideo|String `path`[video path], VideoQuality `quality`[compressed video quality], bool `deleteOrigin`[delete the origin video], int `startTime`[compression video start time], int `duration`[compression video duration from start time], bool `includeAudio`[is include audio in compressed video], int `frameRate`[compressed video frame rate]|compression video at origin video `path`|`Future<MediaInfo>`|
|cancelCompression|`none`|cancel compressing|`Future<void>`|
|deleteAllCache|`none`|Delete all files generated by 'video_compress' will delete all files located at 'video_compress'|`Future<bool>`|

## Subscriptions
|Subscriptions|Description|Stream|
|--|--|--|
|compressProgress$|Subscribe the compression progress steam|double `progress`|

## Contribute

Contributions are always welcome!
<!-- Please read the [contribution guidelines](contributing.md) first. -->

## acknowledgment

Inspired by the flutter_ffmpeg library.
https://github.com/rurico/flutter_video_compress

## Contributors ✨

Thanks goes to these wonderful people:

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="http://projectmeet.app"><img src="https://avatars1.githubusercontent.com/u/42075898?v=4" width="100px;" alt=""/><br /><sub><b>khainhero</b></sub></a><br /><a href="#maintenance-khainhero" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://github.com/Serdnad"><img src="https://avatars1.githubusercontent.com/u/4723453?v=4" width="100px;" alt=""/><br /><sub><b>Andres Gutierrez</b></sub></a><br /><a href="#maintenance-Serdnad" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://github.com/jonataslaw"><img src="https://avatars2.githubusercontent.com/u/35742643?v=4" width="100px;" alt=""/><br /><sub><b>Jonny Borges</b></sub></a><br /><a href="https://github.com/jonataslaw/VideoCompress/commits?author=jonataslaw" title="Code">💻</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!
