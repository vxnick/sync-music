# sync-music
_A simple playlist-to-directory sync utility._

This utility has been created to make synchronising music from a machine to
mobile devices easier.

To replicate my setup, you will need to install
[BitTorrent Sync](http://www.getsync.com/) or similiar, and have it monitor
the `output_dir` specified in the script.

You will then need to install BTSync on your mobile device and point it at your
desired directory. I also enable _Auto Sync_ within the
client and create the share as read-only.

## Notes

**This has been developed with Python 3.4 and is completely untested on any other
version.**

If your `output_dir` is on the same filesystem as your `music_dir` then
`sync-music` will hardlink your tracks to avoid duplication; otherwise it will
create copies of each track. Assuming both your `music_dir` and `output_dir` are
within your home directory, you don't need to worry about this.

## Usage

1. Download the `sync-music` script and put it somewhere in your `PATH`
2. Modify the `music_dir` and `output_dir` values within the script
3. Run `sync-music` to create the initial directory structure for `output_dir`
4. Export one or more M3U playlists to `output_dir/_Playlists`
5. Run `sync-music` to scan and sync the playlist tracks

When you want to re-sync, repeat steps 4 and 5.

```
usage: sync-music [-h] [-n] [-v]

sync playlist music tracks

optional arguments:
  -h, --help     show this help message and exit
  -n, --dry-run  run without making any changes
  -v, --verbose  show more output
```
