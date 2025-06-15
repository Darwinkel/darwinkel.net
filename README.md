# darwinkel.net

Jekyll source files for <https://darwinkel.net> and <https://laroccidentis.nl>.

The web server is configured with some redirects to make sure users land on the right pages for each website.

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
