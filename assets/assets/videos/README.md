# Lookbook clips

Drop MP4 files here and the feed plays them. A post falls back to its still
image — with a slow scale-and-drift — until its clip exists, so the app works
whether or not this folder has anything in it.

## Naming

The filename must match the post's product id, which is set in
`lib/data/sources/catalogue.dart`:

```
rougea.mp4
serelune.mp4
olivia.mp4
celestine.mp4
jolie.mp4
```

## Getting the files

The clips are the brand's own Instagram Reels, and they have to be exported by
hand — Instagram serves its reel pages behind a login wall, and the video URLs
it does hand out are signed and expire within hours, so nothing can fetch them
on our behalf and nothing that pointed at them would keep working.

From the account that owns the posts:

1. Instagram → Settings → Your activity → Download your information.
2. Request a download of **Posts** (or the whole account) in a format that
   includes media.
3. Take the reel MP4s out of the export and rename them as above.

Original files from whoever shot the campaign are better still: they skip
Instagram's re-compression.

## Format

- **MP4 / H.264 + AAC** — the one combination every browser and both mobile
  platforms play.
- **Portrait 9:16**, 1080×1920. The feed crops with `BoxFit.cover`, so a
  landscape clip loses its sides.
- **Under ~8 MB each.** These download over the network on web; a 50 MB clip
  means a viewer stares at a still while it loads.
- Trim to roughly 5–15 seconds. Playback loops.

Clips play muted, which is what browsers require for autoplay.
