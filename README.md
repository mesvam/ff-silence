Fast forward through silences and quiet parts of audio. This is especially useful on videos where the speaker uses many long pauses. Activate with Ctrl+A or enable by default using the `enabled` option (add `script-opts-append=ff_silence-enabled=true` to `mpv.conf`)

## How it works

Silences are detected by ffmpeg's `silencedetect` filter when the volume is below `silence_threshold` for a duration longer than `silence_duration`. When a silence is found, the playback speed is increased by a constant multiplicative factor `speedup` until audio is found.

## Options

These can be set as script options, e.g.
`--script-opts-append=silence_threshold=-18`

- `enabled`: set to `true` to enable at startup (default `false`)
- `speedup`: speedup factor during silences (default 2.83)
- `silence_threshold`: volume threshold (in dB) that will be detected as silence (default -23)
- `silence_duration`: minimum duration (in seconds) that will be detected as silence (default 0.25)
- `speed_change_osd`: set to `true` to display an indicator every time the speed changes (default `false`)
- `debug`: set to `true` to show debug output on the commandline (default `false`)

Some parameters can be adjusted during playback with the following default key bindings

- Ctrl+A = toggle
- Alt++ = increase `speedup`
- Alt+- = decrease `speedup`
- Ctrl+* = increase `silence_threshold`
- Ctrl+/ = decrease `silence_threshold`
- Alt+* = increase `silence_duration`
- Alt+/ = decrease `silence_duration`
