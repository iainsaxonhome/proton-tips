# Steam Games

If game audio crackles or drops out use this for the game launcher settings in Steam: `PULSE_LATENCY_MSEC=60 %command%`.

# ALSA Config

It seems to make things easier to just lock the system audio to 48000KHz.

Add this file to `~/.asoundrc` to set the new default frequency:

```
pcm.!default {
    type plug
    slave.pcm "device"
}

pcm.device{
        format S24_LE
        rate 48000
        type hw
        card 0
        device 1
}
```

It might need tweaking to use the correct card and device numbers and these can be found via: `alsactl info`.
