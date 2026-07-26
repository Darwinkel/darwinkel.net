# darwinkel.net

Jekyll source files for <https://darwinkel.net> and <https://laroccidentis.nl>.

The web server is configured with some redirects to make sure users land on the right pages for each website.
It also has HTTP/3 and Brotli compression enabled.

The websites are pure responsive HTML and CSS, with everything being self-hosted. No external network calls.
Structured metadata and semantic tags are used and valid.

Feel free to make issues or PRs. They're welcome for both technical matters as well as content.

## Dependencies

- Ruby
- Ruby Bundler

## Build instructions

- `bundle install`
- `bundle update`
- `bundle exec jekyll build`

Use `bundle exec jekyll serve` for a development webserver.

## Changes from Jekyll Minima

CDN is replaced by self host :)

See `assets/*` folder and `_includes/*`.

## Image compression

Use `cwebp` to optimize images for web distribution. Below reduces a 5.5MB photo to 0.5MB.

```sh
cwebp -q 100 -m 6 -mt -metadata none -resize 1020 0 vines_mid_june.jpg -o vines_mid_june.webp
```

To convert all `jpg` files:

```sh
for f in *.jpg; do cwebp -q 100 -m 6 -mt -metadata none -resize 1020 0 "$f" -o "${f%.jpg}.webp"; done
```

## Video compression

Use `ffmpeg` to optimize videos for web distribution. Below reduces a 5.8MB video to 2.6MB.

```sh
for f in *.mp4; do ffmpeg -i "$f"   -c:v libsvtav1   -crf 24   -preset 4   -pix_fmt yuv420p10le   -svtav1-params tune=0   -c:a libopus   -b:a 128k   -vbr on   -compression_level 10   "${f%.mp4}.webm"; done
```