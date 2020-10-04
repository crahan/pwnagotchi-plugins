# Pwnagotchi plugins

## Introduction

These are customized versions of the GPS and Memtemp Pwnagotchi plugins and include the functionality introduced in [Pwnagotchi](https://github.com/evilsocket/pwnagotchi) pull requests [#918](https://github.com/evilsocket/pwnagotchi/pull/918) and [#919](https://github.com/evilsocket/pwnagotchi/pull/919) (pending approval). The plugin versions in this repo are more tailored to my specific use case/liking (e.g. different line spacing defaults) and only include default position values for the Waveshare v2 e-ink display (i.e. hardware I can properly test).

The idea behind pull requests [#918](https://github.com/evilsocket/pwnagotchi/pull/918) and [#919](https://github.com/evilsocket/pwnagotchi/pull/919) is to better align the positioning and line spacing of the GPS and Memtemp plugins (as I use these together) and to provide additional configuration options to tweak the output (e.g. `position`, `linespacing`).

If you still want to use this code and you're not using a Waveshare v2 e-ink display or the fallback values don't work for you, I recommend using the new `position` and `linespacing` configuration properties to tweak the default position setting. Feel free to submit a pull request with some sane defaults for your display though, so I can update the code accordingly.

## Installation

To use these plugins, clone this repository to your Pwnagotchi and point `main.custom_plugins` in `/etc/pwnagotchi/config.toml` to the repository folder. Please note that the plugins in this repository are named `memtemp-plus` and `gps-plus` so they don't interfere with the default plugins included with the Pwnagotchi code.

## gps-plus

New features:
- add `position` configuration option
- add `linespacing` configuration option
- set defaults to properly align with Memtemp plugin output

Sample configuration:
```
main.plugins.gps-plus.enabled = true
main.plugins.gps-plus.speed = 4800
main.plugins.gps-plus.device = "/dev/ttyUSB0"
main.plugins.gps-plus.position = "122,70"
main.plugins.memtemp-plus.linespacing = 12 
```

## memtemp-plus

New features:
- add `position` configuration option
- add `linespacing` configuration option
- new `freq` CPU frequenty field
- option to configure up to 3 fields with a custom order (i.e. mem, cpu, temp, and freq)
- set defaults to properly align with GPS plugin output

Sample configuration:
```
main.plugins.memtemp-plus.enabled = true
main.plugins.memtemp-plus.scale = "celsius"
main.plugins.memtemp-plus.orientation = "vertical"
main.plugins.memtemp-plus.fields = "mem,cpu,temp"
main.plugins.memtemp-plus.position = "200,70"
main.plugins.memtemp-plus.linespacing = 12 
```
