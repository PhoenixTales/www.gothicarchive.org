# Contributing

## Online vs offline deployment
Gothic Archive uses HTML interface for both online web version, and local offline access from extracted zip archive.
In offline archive, text and media files are together in single directory structure.
Online web version for performance reasons uses separate servers for each type of assets:
- [`www`](https://github.com/PhoenixTales/www.gothicarchive.org) (text, markdown and html)
- [`audio`](https://github.com/PhoenixTales/audio.gothicarchive.org)
- [`images`](https://github.com/PhoenixTales/images.gothicarchive.org)
- [`videos`](https://github.com/PhoenixTales/videos.gothicarchive.org)
- [`bin`](https://github.com/PhoenixTales/bin.gothicarchive.org) (other non-textual file types)

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
- hardcode domain name, like `https://images.gothicarchive.org/img/foo.jpg` (because that won't work in offline archive)
- use relative path, like `../img/foo.jpg` (because that won't work in online web version, where pages and media assets are on different servers)

Instead of that, special URL variables have to be used. Replace with them the first part of URL with something `{{ likeThis }}`, so that it will turn into the right form both in online and offline version.


### Variables constructing URLs

Template `path-variables.liquid` defines variables that need to be used when writing URLs:
- `{{ wwwRoot }}`    / `{{ wwwDir }}`    (for page and text file URLs)
- `{{ audioRoot }}`  / `{{ audioDir }}`  (for audio URLs)
- `{{ binRoot }}`    / `{{ binDir }}`    (for URLs of files you can't open in the browser)
- `{{ imagesRoot }}` / `{{ imagesDir }}` (for image URLs)
- `{{ videosRoot }}` / `{{ videosDir }}` (for video URLs)
- `{{ wikiRoot }}`   / `{{ wikiDir }}`   (for wiki URLs)

Use Root variable for absolute URLs and Dir variable for URLs relative to current page.


### Examples #1

- `{{ wwwDir }}` - expands to directory with current page, for example `https://gothicarchive.org/comic` or `C:\marvin\gothicarchive\comic`
- `{{ wwwRoot }}` - expands to root of archive, for example `https://gothicarchive.org` or `C:\marvin\gothicarchive`
- `{{ imagesDir }}` - expands to images directory corresponding to directory with current page, for example `https://images.gothicarchive.org/comic` or `C:\marvin\gothicarchive\images\comic`
- `{{ imagesRoot }}` - expands to images root of archive, for example `https://images.gothicarchive.org` or `C:\marvin\gothicarchive\images`
- `{{ wwwRoot }}/page.html` expands to `https://gothicarchive.org/page.html` or `C:\marvin\gothicarchive\page.html`
- `{{ wwwDir }}/page.html` when inside page `/articles/news` expands to `https://gothicarchive.org/articles/news/page.html` or `C:\marvin\gothicarchive\articles\news\page.html`
- `{{ imagesDir }}/cover.jpg` when inside page `/articles/news` expands to `https://images.gothicarchive.org/articles/news/cover.jpg` or `C:\marvin\gothicarchive\images\articles\news\cover.jpg`
- `{{ imagesRoot }}/cover.jpg` expands to `https://images.gothicarchive.org/cover.jpg` or `C:\marvin\gothicarchive\images\cover.jpg`

These URLs cannot be written directly in absolute form ("whole") by hand, because we need the first part to be different when page is loaded from our web domain (gothicarchive.org) and different when loaded from local copy of archive (gothicarchive.zip).


### Examples #2

Bad urls:
- `<a href="https://gothicarchive.org/page.html">Link</a>` (will not work from offline .zip)
- `<img src="../images/picture.jpg">` (will not work from http .org)
- `<img src="{{ wwwDir }}/picture.jpg">` (image url but uses www variable)

Good urls:
- `<a href="{{ wwwRoot }}/page.html">Link</a>`
- `<img src="{{ imagesDir }}/picture.jpg">`


### Examples #3
We are editing file:
```
www.gothicarchive.org/comic/gothic/content_gothic.html
```
and need to link the file
```
images.gothicarchive.org/comic/img/gothic/gothic_logo.gif
```
Correct:
```
<img src="{{ imagesDir }}/../img/gothic/gothic_logo.gif">
```
Discouraged (works, but has to be updated every time `/comic/` is moved or renamed):
```
<img src="{{ imagesRoot }}/comic/img/gothic/gothic_logo.gif">
```
Incorrect (will not work in the offline archive):
```
<img src="https://images.gothicarchive.org/comic/img/gothic/gothic_logo.gif">
```
Incorrect (will only work in the offline archive):
```
<img src="../img/gothic/gothic_logo.gif">
```
Incorrect (will always give broken `/comic/gothic/comic/img/gothic`):
```
<img src="{{ imagesDir }}/comic/img/gothic/gothic_logo.gif">
```


### More about path-variables

`path-variables.liquid` is written in Liquid Template Language, documented at [shopify.dev/docs/api/liquid](https://shopify.dev/docs/api/liquid) .
We use it, because it is supported out-of-the-box by Jekyll, which is supported out-of-the-box by GitHub Pages.
In this language, every line of code has to be surrounded with `{ % -` and `- % }` (but without spaces between these symbols).
To make reading easier, we put both start and end at the end of the lines.
GitHub uses rather old version of this language. Not all the features of it work.
