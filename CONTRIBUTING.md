# Contributing

## Online vs offline deployment
Gothic Archive uses HTML interface for both online web version, and local offline access from extracted zip archive.
In offline archive, text and media files are together in single directory structure.
Online web version for performance reasons uses separate server for heavy media assets (`media.gothicarchive.org`) and for txt/html/md files (`gothicarchive.org`). This way changes to text and code are reflected online very quickly, in less than one minute after commit is merged to `main` branch. On the other hand, the heavy media assets take significant time to deploy and invalidate CDN caches, so you may have to wait many minutes before changes are visible online.

### How to check progress of online deployment?
- for text and code: https://github.com/PhoenixTales/web.gothicarchive.org/actions
- for media assets: https://github.com/PhoenixTales/media.gothicarchive.org/actions

Click on the top item to see detailed progress. If deployment shows as finished, but file URL still shows old content, try bypassing caches by adding `?nocache=<some random number>` at the end of URL. If you get correct content this time, it means that you have to clear your browser cache or wait until CDN cache is refreshed.

## URLs
All internal URLs that appear in archive content (in particular, `<img src="`>) cannot either:
- hardcode domain name, like `https://media.gothicarchive.org/img/foo.jpg` (because that won't work in offline archive)
- use relative path, like `../img/foo.jpg` (because that won't work in online web version, where pages and media assets are on different servers)

Instead of that, special URL macros have to be used.

### Macros for URLs of text/html/md files
- `linkBase` - will expand to directory with current page, for example `https://gothicarchive.org/comix` or `C:\marvin\gothicarchive\comix`
- `absLinkBase` - will expand to root of archive, for example `https://gothicarchive.org` or `C:\marvin\gothicarchive`

### Macros for URLs of media assets 
- `mediaLinkBase` - will expand to media directory corresponding to directory with current page, for example `https://media.gothicarchive.org/comix` or `C:\marvin\gothicarchive\comix`
- `absMediaLinkBase` - will expand to media root of archive, for example `https://media.gothicarchive.org` or `C:\marvin\gothicarchive`

### Examples
We are editing file:
```
web.gothicarchive.org/comix/gothic/content_gothic.html
```
and need to link the file
```
media.gothicarchive.org/comix/img/gothic/gothic_logo.gif
```
Correct (in this case, `../` have to be used to correct the URL, otherwise, it will be `web.gothicarchive.org/comix/gothic/img/gothic/gothic_logo.gif`):
```
<img src="{{ mediaLinkBase }}/../img/gothic/gothic_logo.gif">
```
Acceptable (has to be updated every time `/comix/` is moved or renamed):
```
<img src="{{ absMediaLinkBase }}/comix/img/gothic/gothic_logo.gif">
```
Incorrect (will not work in offline archive):
```
<img src="https://media.gothicarchive.org/comix/img/gothic/gothic_logo.gif">
```
Incorrect (will only work in offline archive):
```
<img src="../img/gothic/gothic_logo.gif">
```
Incorrect (will always give broken `/comix/gothic/comix/img/gothic`):
```
<img src="{{ mediaLinkBase }}/comix/img/gothic/gothic_logo.gif">
```
