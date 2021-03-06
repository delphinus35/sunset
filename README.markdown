Version: 1.0.3  
Last Change: 2012 Oct 20

# Sunset

## Introduction

Sunset automatically sets `background` when the sun rises and sets, and also when you start Vim. When the sun is up, or rises, it'll `set background=light` and when the sun is down, or sets, it'll `set background=dark`.

So as not to interrupt you, Sunset waits for four seconds (on the `CursorHold` event) after you've pressed a key or left insert mode before changing the background. If you change your background during the day or night, it'll respect that.

You must set some options in your `.vimrc` for Sunset to work, so please read on for details.

If you feel that Sunset can be improved, pull requests and issues are appreciated and humbly requested.

## Installation

If you don't already have a preferred installation method, I recommend installing [Vundle](http://github.com/gmarik/vundle). Once done, add the declaration for Sunset to your `.vimrc`:

```vim
Bundle 'amdt/sunset'
```

And install:

```vim
:BundleInstall
```

*Note:* other installation methods are detailed in the included documentation.

## Requirements

* Sunset requires Vim 7.3
* Vim compiled with `+float` support. Use `:version` to check if this feature is available in your build.
* Requires a system with `strftime()`, with the following format options:
    - %j returns the current day of the year.
    - %H returns the current hour of the day in 24-hour time.
    - %M returns the current minute of the hour.
* A colorscheme with light and dark variants, such as [Solarized](http://github.com/altercation/vim-colors-solarized) or [Hemisu](http://github.com/noahfrederick/Hemisu).

## Configuration

*Note:* If you push your dotfiles to Github, please see the section titled 'A Reminder on Privacy'.

### g:sunset\_latitude & g:sunset\_longitude

The latitude and longitude of your location in decimal. Values North and East must be positive values, those South and West must be negative.

London, for example, lies at 51 degrees, 30 minutes North; and 7 minutes West.

In decimal, this is 51.5 degrees North, 0.1167 degrees West.

If you lived in London, you might set these options as follows:

```vim
let g:sunset_latitude = 51.5
let g:sunset_longitude = -0.1167
```

If you lived in Tokyo (35 degrees, 40 minutes and 12 seconds North; 139 degrees, 46 minutes and 12 seconds East), you might set these options as follows:

```vim
let g:sunset_latitude = 35.67
let g:sunset_longitude = 139.8
```

*Note:* Don't forget, negative values South and West.

### g:sunset\_utc\_offset

The difference in hours between your timezone and Coordinated Universal Time.

For example:

```vim
let g:sunset_utc_offset = 0 " London
let g:sunset_utc_offset = 1 " London (British Summer Time)
let g:sunset_utc_offset = 9 " Tokyo
```

*Note:* Sunset does not handle any daylight savings civil times.

## A Reminder of Privacy

For those of us who publish our dotfiles on Github etc., please take this as a gentle reminder that out of habit you might be about to publish your whereabouts to the greater public. If this concerns you, using the location of your nearest large city might suffice; Sunset will be plenty accurate enough.

## License

Sunset is distributed under the same terms as Vim itself. See `:help license` for details.
