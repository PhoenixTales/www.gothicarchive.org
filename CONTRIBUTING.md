# Contributing

## Online vs offline deployment
Gothic Archive uses HTML interface for both online web version, and local offline access from extracted zip archive.
In offline archive, text and media files are together in single directory structure.
Online web version for performance reasons uses separate servers for each type of assets:
- audio
- images
- videos
- bin (other non-textual file types)

This way most changes are reflected online very quickly, in less than one minute after commit is merged to `main` branch. 
On the other hand, changes to heaviest repositories (e.g. images) take significant time to deploy and invalidate CDN caches, so you may have to wait many minutes before changes are visible online.

### How to check progress of online deployment?
- for text and code: https://github.com/PhoenixTales/www.gothicarchive.org/actions
- for audio: https://github.com/PhoenixTales/audio.gothicarchive.org/actions
- for images: https://github.com/PhoenixTales/images.gothicarchive.org/actions
- for videos: https://github.com/PhoenixTales/videos.gothicarchive.org/actions
- for binary files: https://github.com/PhoenixTales/bin.gothicarchive.org/actions

Click on the top item to see detailed progress. If deployment shows as finished, but file URL still shows old content, try bypassing caches by adding `?nocache=<some random number>` at the end of URL. If you get correct content this time, it means that you have to clear your browser cache or wait until CDN cache is refreshed.

## URLs
All internal URLs that appear in archive content (in particular, `<img src="`>) cannot either:
- hardcode domain name, like `https://media.gothicarchive.org/img/foo.jpg` (because that won't work in offline archive)
- use relative path, like `../img/foo.jpg` (because that won't work in online web version, where pages and media assets are on different servers)

Instead of that, special URL macros have to be used.

### Variables constructing URLs
- `wwwDir` - will expand to directory with current page, for example `https://gothicarchive.org/comix` or `C:\marvin\gothicarchive\comix`
- `wwwRoot` - will expand to root of archive, for example `https://gothicarchive.org` or `C:\marvin\gothicarchive`
- `imagesDir` - will expand to images directory corresponding to directory with current page, for example `https://images.gothicarchive.org/comix` or `C:\marvin\gothicarchive\comix`
- `imagesRoot` - will expand to images root of archive, for example `https://images.gothicarchive.org` or `C:\marvin\gothicarchive\images`
- for audio, videos and bin, it works similarly as for images in examples below
- see [path-variables.html](_templates\path-variables.html) for more information

### Examples
We are editing file:
```
web.gothicarchive.org/comix/gothic/content_gothic.html
```
and need to link the file
```
images.gothicarchive.org/comix/img/gothic/gothic_logo.gif
```
Correct:
```
<img src="{{ imagesDir }}/../img/gothic/gothic_logo.gif">
```
Acceptable (has to be updated every time `/comix/` is moved or renamed):
```
<img src="{{ imagesRoot }}/comix/img/gothic/gothic_logo.gif">
```
Incorrect (will not work in the offline archive):
```
<img src="https://images.gothicarchive.org/comix/img/gothic/gothic_logo.gif">
```
Incorrect (will only work in the offline archive):
```
<img src="../img/gothic/gothic_logo.gif">
```
Incorrect (will always give broken `/comix/gothic/comix/img/gothic`):
```
<img src="{{ imagesDir }}/comix/img/gothic/gothic_logo.gif">
```
