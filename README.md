# tzdiff

Displays Timezone differences with localtime in CLI (shell script)

## Tzdiff or Timediff ?

This command was originally "timediff". Now, it's "tzdiff" because of naming conflict.

## Usage

    tzdiff [-0] [-n count] [-f format] [-t time] timezone [timezone ...] [count] [0]

Tzdiff with no arguments will display list of timezones.
Tzdiff with timezone will display the time differences of remote time with local time.

### Options

* -h: show usage
* -0: round down to hour
* -n count: max hours (default: 10)
* -f format: output format (using '+output_fmt' of date(1))
* -t time: set the start time instead of current time.
 'YYYY-mm-ddTHH:MM' or 'YYYYmmddTHHMM' is ok.
* -H: beccom the scripting mode. Fields are explicitly separated by single tab instead of an arbitrary space.

## Install

### FreeBSD

You can easy to install pkg or ports.

Using pkg

   $ sudo pkg install tzdiff

Using ports

   $ sudo portsnap auto
   $ cd /usr/ports/misc/tzdiff
   $ sudo make install && sudo make clean

### macOS

MacPorts (may be soon)

   $ sudo port sync
   $ sudo port install tzdiff

Homebrew

   $ brew tap belgianbeer/minmin
   $ brew install tzdiff

### Debian / Ubuntu (may be soon)

   $ sudo apt update
   $ sudo apt install tzdiff

## Example (Author's timezone is JST)

    $ tzdiff
    Africa/         Australia/      Etc/            MST             WET
    America/        CET             Europe/         MST7MDT         posixrules
    Antarctica/     CST6CDT         Factory         PST8PDT         zone.tab
    Arctic/         EET             HST             Pacific/
    Asia/           EST             Indian/         SystemV/
    Atlantic/       EST5EDT         MET             UTC

    $ tzdiff America/Los_Angeles
    America/Los_Angeles
    2017-05-12 05:55 PDT    2017-05-12 21:55 JST
    2017-05-12 06:55 PDT    2017-05-12 22:55 JST
    2017-05-12 07:55 PDT    2017-05-12 23:55 JST
    2017-05-12 08:55 PDT    2017-05-13 00:55 JST
    2017-05-12 09:55 PDT    2017-05-13 01:55 JST
    2017-05-12 10:55 PDT    2017-05-13 02:55 JST
    2017-05-12 11:55 PDT    2017-05-13 03:55 JST
    2017-05-12 12:55 PDT    2017-05-13 04:55 JST
    2017-05-12 13:55 PDT    2017-05-13 05:55 JST
    2017-05-12 14:55 PDT    2017-05-13 06:55 JST

Tzdiff supports TIMEZONE's completion. For example,

    $ tzdiff Lon             # enter RETURN instead of TAB
    Arctic/Longyearbyen     Europe/London

    $ tzdiff Lond
    Europe/London
    2017-05-31 07:10 BST    2017-05-31 15:10 JST
    2017-05-31 08:10 BST    2017-05-31 16:10 JST
    2017-05-31 09:10 BST    2017-05-31 17:10 JST
    2017-05-31 10:10 BST    2017-05-31 18:10 JST
    2017-05-31 11:10 BST    2017-05-31 19:10 JST
    2017-05-31 12:10 BST    2017-05-31 20:10 JST
    2017-05-31 13:10 BST    2017-05-31 21:10 JST
    2017-05-31 14:10 BST    2017-05-31 22:10 JST
    2017-05-31 15:10 BST    2017-05-31 23:10 JST
    2017-05-31 16:10 BST    2017-06-01 00:10 JST

    $ tzdiff New_ 0 5
    America/New_York
    2017-05-12 08:00 EDT    2017-05-12 21:00 JST
    2017-05-12 09:00 EDT    2017-05-12 22:00 JST
    2017-05-12 10:00 EDT    2017-05-12 23:00 JST
    2017-05-12 11:00 EDT    2017-05-13 00:00 JST
    2017-05-12 12:00 EDT    2017-05-13 01:00 JST

It is easy to check changes from daylight saving time to standard time

    $ tzdiff -t 2017-11-05T11:00 Los New_ Brus
    America/Los_Angeles     America/New_York        Europe/Brussels
    2017-11-04 19:00 PDT    2017-11-04 22:00 EDT    2017-11-05 03:00 CET    2017-11-05 11:00 JST
    2017-11-04 20:00 PDT    2017-11-04 23:00 EDT    2017-11-05 04:00 CET    2017-11-05 12:00 JST
    2017-11-04 21:00 PDT    2017-11-05 00:00 EDT    2017-11-05 05:00 CET    2017-11-05 13:00 JST
    2017-11-04 22:00 PDT    2017-11-05 01:00 EDT    2017-11-05 06:00 CET    2017-11-05 14:00 JST
    2017-11-04 23:00 PDT    2017-11-05 01:00 EST    2017-11-05 07:00 CET    2017-11-05 15:00 JST
    2017-11-05 00:00 PDT    2017-11-05 02:00 EST    2017-11-05 08:00 CET    2017-11-05 16:00 JST
    2017-11-05 01:00 PDT    2017-11-05 03:00 EST    2017-11-05 09:00 CET    2017-11-05 17:00 JST
    2017-11-05 01:00 PST    2017-11-05 04:00 EST    2017-11-05 10:00 CET    2017-11-05 18:00 JST
    2017-11-05 02:00 PST    2017-11-05 05:00 EST    2017-11-05 11:00 CET    2017-11-05 19:00 JST
    2017-11-05 03:00 PST    2017-11-05 06:00 EST    2017-11-05 12:00 CET    2017-11-05 20:00 JST

Tzdiff works with the following operating systems.

* macOS / FreeBSD / NetBSD / OpenBSD (It may work on DragonFly BSD.)
* Debian / Ubuntu / CentOS and many Linux distros
* Windows subsystem for Linux
