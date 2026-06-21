# Thumpi site

Static GitHub Pages site using Jekyll collections for songs, lyrics, and thoughts.

## What changed

- `thoughts.html` now lists posts from `_posts/`.
- `songs.html` now lists songs from `_songs/` grouped by album/release.
- `lyrics.html` now renders lyrics from the same `_songs/` files.
- Each song gets its own page at `/songs/song-name/`.
- Audio previews are external URLs in each song file, rendered with the browser's native `<audio>` player.
- `.pages.yml` is included for Pages CMS, so a non-technical editor can add thoughts and songs through a browser UI.

## Album order

Album/release order is controlled by `_data/albums.yml`:

```yml
- name: "blue to the pop"
  order: 1
```

The `name` must match the `album` value in the song file. Lower `order` numbers appear first. Songs with no `album` value appear under `non-album tracks`. Songs with an album value that is missing from `_data/albums.yml` appear under `other releases` so they are not accidentally hidden.

## Adding a song manually

Create a file in `_songs/`, for example:

```md
---
title: "Song title"
date: 2026-06-06
album: "Release name"
track: 1
preview_mp3: "https://your-file-server.example/thumpi/previews/song-title.mp3"
bandcamp_url: "https://thumpi.bandcamp.com/"
spotify_url: ""
youtube_url: ""
soundcloud_url: ""
bandcamp_embed_url: ""
published: true
lyrics: |
  First lyric line
  Second lyric line

  Another verse
---
```

Use external audio URLs for previews. Do not put full audio libraries in this repository.

## Adding a thought/blog post manually

Create a file in `_posts/`, for example:

```md
---
title: "small update"
date: 2026-06-06
---

Write the post here.
```

## Pages CMS

The `.pages.yml` file defines two editable sections:

- Thoughts / blog
- Songs and lyrics

The artist should only need to fill in title, date, preview URL, links, and lyrics. Layout files and CSS should be left alone unless the site design is being changed.

## Favicon

`favicon.ico` and `icon.png` are linked from the default layout. Browsers should stop requesting a missing `/favicon.ico` as long as those files stay in the repository root.
