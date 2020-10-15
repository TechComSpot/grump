# grump

![](screenshot.png)

```
Great but
Really
Ugly
Media
Player
```

A very minimal CLI audio player.

## Features

* cross-platform
* ID3 tag scanning
* Supports
	* FLAC
	* MP3
	* OGG/Vorbis
	* WAV
* Tag Editor
* Quick Ratings
* Playback Effects (speed up/down)

## Install

### Linux

```sh
sudo apt install libasound2-dev build-essential
go get github.com/dhulihan/grump
```

### Mac OSX

```sh
brew tap dhulihan/grump
brew install grump
```

Alternatively, you can install the latest (possibly unreleased) version:

```sh
go get github.com/dhulihan/grump
```

* You can also download pre-build binaries on the [releases](https://github.com/dhulihan/grump/releases) page.

## Usage

```
grump path/to/some/audio/files
```

## Keyboard Shortcuts

```
┌───────┬───────────────────────────────────────────────────┐
│space  │pause/unpause                                      │
├───────┼───────────────────────────────────────────────────┤
│escape │stop track                                         │
├───────┼───────────────────────────────────────────────────┤
│d      │describe currently playing track                   │
├───────┼───────────────────────────────────────────────────┤
│e      │edit currently playing track                       │
├───────┼───────────────────────────────────────────────────┤
│delete │delete currently playing track (with prompt)       │
├───────┼───────────────────────────────────────────────────┤
│l      │view logs page                                     │
├───────┼───────────────────────────────────────────────────┤
│left   │seek forward (does not work on flac)               │
├───────┼───────────────────────────────────────────────────┤
│right  │seek backward  (does not work on flac)             │
├───────┼───────────────────────────────────────────────────┤
│]      │play next track                                    │
├───────┼───────────────────────────────────────────────────┤
│[      │play previous track                                │
├───────┼───────────────────────────────────────────────────┤
│=      │volume up                                          │
├───────┼───────────────────────────────────────────────────┤
│-      │volume down                                        │
├───────┼───────────────────────────────────────────────────┤
│+      │speed up                                           │
├───────┼───────────────────────────────────────────────────┤
│_      │speed down                                         │
├───────┼───────────────────────────────────────────────────┤
│q      │quit                                               │
├───────┼───────────────────────────────────────────────────┤
│0      │set rating of currently playing track to 🌑        │
├───────┼───────────────────────────────────────────────────┤
│1      │set rating of currently playing track to 🌕        │
├───────┼───────────────────────────────────────────────────┤
│2      │set rating of currently playing track to 🌕🌕      │
├───────┼───────────────────────────────────────────────────┤
│3      │set rating of currently playing track to 🌕🌕🌕    │
├───────┼───────────────────────────────────────────────────┤
│4      │set rating of currently playing track to 🌕🌕🌕🌕  │
├───────┼───────────────────────────────────────────────────┤
│5      │set rating of currently playing track to 🌕🌕🌕🌕🌕│
├───────┼───────────────────────────────────────────────────┤
```

## Configuration

grump will load a `~/.grump.yaml` file if present.

```yaml
# log level. options: trace, debug, info, warn, error
log_level: info

# if true, write application logs to a file
log_to_file: false

# write logs to this file, if enabled
log_file: grump.log
```

## Development

### Building

```sh
# build for linux (linux host)
./scripts/build-linux.sh

# build for linux (non-linux host)
docker-compose run build

# build for darwin (darwin host)
./scripts/build-darwin.sh
```

### Releasing

```sh
VERSION=0.0.0
git tag $VERSION
git push origin $VERSION
goreleaser release --rm-dist
```
