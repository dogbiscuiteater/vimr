VimR — Neovim Refined
==================

![App Icon](https://raw.github.com/qvacua/vimr/master/resources/vimr-app-icon.png)

[Download](https://github.com/qvacua/vimr/releases) • <http://vimr.org>

[![Bountysource](https://www.bountysource.com/badge/team?team_id=933&style=raised)](https://www.bountysource.com/teams/vimr?utm_source=VimR%20%E2%80%94%20Vim%20Refined&utm_medium=shield&utm_campaign=raised) [![Chat at https://gitter.im/vimr/vimr](https://badges.gitter.im/vimr/vimr.svg)](https://gitter.im/vimr/vimr?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Travis builds](https://travis-ci.org/qvacua/vimr.svg?branch=develop)](https://travis-ci.org/qvacua/vimr) [![Stories in Ready](https://badge.waffle.io/qvacua/vimr.svg?label=ready&title=Ready)](http://waffle.io/qvacua/vimr)

![Screenshot 1](https://raw.githubusercontent.com/qvacua/vimr/develop/resources/screenshot1.png)
![Screenshot 0](https://raw.githubusercontent.com/qvacua/vimr/develop/resources/screenshot0.png)
![Screenshot 2](https://raw.githubusercontent.com/qvacua/vimr/develop/resources/screenshot2.png)

## About

Project VimR is an attempt to refine the Neovim experience (or just YA Neovim GUI for mac OS). The goal is to build an editor that uses Neovim inside with many of the convenience GUI features similar to those present in modern editors. We mainly use Swift, but also use Objective-C when its C-nature helps.

There are other working Neovim GUIs for OS X, e.g. [NyaoVim](https://github.com/rhysd/NyaoVim), [neovim-dot-app](https://github.com/rogual/neovim-dot-app), etc., why another?

- play around (obviously) with [Neovim](https://github.com/qvacua/neovim),
- play around with Swift (and especially with [RxSwift](https://github.com/ReactiveX/RxSwift)) and
- (most importantly) have fun!

### NvimView

[NvimView](https://github.com/qvacua/vimr/tree/master/NvimView) is VimR's Cocoa Framework which bundles everything, e.g. Neovim's `runtime`-files, needed to embed Neovim in a Cocoa App. See the [wiki](https://github.com/qvacua/vimr/wiki/SwiftNeoVim-Framework) for more details.

---

If you want to support VimR financially, you can use [Bountysource](https://www.bountysource.com/teams/vimr). Big thanks to [all](https://www.bountysource.com/teams/vimr/backers) who did support: We list our spendings in the [wiki](https://github.com/qvacua/vimr/wiki/How-we-use-the-donations).

## Download

Pre-built binaries can be found under [Releases](https://github.com/qvacua/vimr/releases).

## Implemented Features

* Multiple windows.
* Basic input including Emojis and Hangul (+Hanja): We don't know whether other input systems work...
* Markdown preview
* Generic HTML preview (retains the scroll position when reloading)
* Basic mouse support: Left button actions and scrolling.
* Fuzzy file finder a la Xcode's "Open Quickly..."
* Basic trackpad support: Pinching for zooming and two-finger scrolling.
* Ligatures: Turned off by default. Turn it on in the Preferences.
* Basic File and Edit menu items.
* Command line tool.
* (Simple) File browser
* Flexible workspace model a la JetBrain's IDEs

We will gradually create feature [issues](https://github.com/qvacua/vimr/issues) with more details. For the current status see the [project board](https://waffle.io/qvacua/vimr).

## How to Build

First after cloning the VimR source tree you need to initialize git submodules

```bash
git submodule init
git submodule update
```

You have to use Xcode 9. First install `homebrew`, then in the project root:

```bash
xcode-select --install # install the Xcode command line tools, if you haven't already
brew bundle

./bin/build_vimr.sh # VimR.app will be placed in build/Build/Products/Release/
```

## Project Setup

### Artifacts Hierarchy

```
VimR.app
+-- NvimView.framework
    +-- NeoVimView
    +-- runtime files for Neovim
    +-- NvimServer
        +-- libnvim
        +-- other libs for Neovim
```

### Libraries for Neovim

* The library `libiconv` is linked by the linker flag `-liconv`. The version bundled with macOS will be linked.
* The library `libintl` is pre-built in `third-party/libintl/lib` and linked by "Other Linker Flags" of the NvimServer target.
* Other libraries used by Neovim, which are automatically built by building `libnvim`, are linked by "Other Linker Flags" of the NvimServer target.

## License

[MIT](https://github.com/qvacua/vimr/blob/master/LICENSE)

---

If you are here for VimR-MacVim, use the [macvim/master](https://github.com/qvacua/vimr/tree/macvim/master) branch and the version [0.8.0 (32)](https://github.com/qvacua/vimr/releases/tag/v0.8.0-32).
