Modified version of the beets built-in [convert plugin](https://github.com/beetbox/beets/blob/master/beetsplug/convert.py) to suit my library:
* Music @ 48kHz or lower goes in `Music/`
* Music any higher goes in `Music-HQ/`, but is also transcoded to `bitrate/2` (i.e. 96 -> 48kHz, 88.2 -> 44.1kHz) and placed in `Music-LQ/`.

To do so, a `max_samplerate` option is added, similar to `max_bitrate`.

In my config, the `paths` section uses the `inline` plugin to decide which or `Music` and `Music-HQ` to put a release in, then the `convert-mod:` subsection has it's own `paths:` which doesn't include a directory, so that `convert-mod:dest` is used.

Additionally, the order of operations (at least with `auto_keep` is changed, so that transcoding is done as the last step and so includes all metadata, no clue why this wasn't the case before.

# License
See convert.py's header.
