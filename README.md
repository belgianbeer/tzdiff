# tzdiff

Displays Timezone differences with localtime in CLI (shell script)

This command was originally "timediff". Now, it's "tzdiff" because of naming conflict.

## Usage

    tzdiff [-0l] [-n count] [-f format] [-t time] timezone [timezone ...] [count] [0]

Tzdiff with no arguments will display list of timezones.
Tzdiff with timezone will display the time differences of remote time with local time.

### Options

* -h: show usage
* -0: round down to hour
* -l: display full timezone name
* -n count: max hours (default: 10)
* -f format: output format (using '+output_fmt' of date(1))
* -t time: set the start time instead of current time.
* -H: became the scripting mode. Fields are explicitly separated by single tab instead of an arbitrary space.
* -HH: became the scripting mode without timzone name.
* -N: display without local timezone.

### -t time

If your system has the GNU date, you can use the flexible format. Otherwise, specify as 'YYYY-mm-ddTHH:MM' or 'YYYYmmddTHHMM' and adding 'Z' at the end makes it UTC.


## Install

### FreeBSD

If you are pkg user, you can easy to install tzdiff like this.

```
$ sudo pkg install tzdiff
```

Of course, it is already in ports. You can easy to play with ports.

### NetBSD and pkgsrs

Tzdiff is registered in pkgsrc. If you use pkgsrc, you can easily install it.

### macOS

If you are MacPorts user, you can easy to install tzdiff.

```
$ sudo port install tzdiff
```

If you are Homebrew user, you can install with personal tap.

```
$ brew tap belgianbeer/minmin
$ brew install tzdiff
```

### Debian / Ubuntu

Tzdiff is registerd in debian pkg, you can easy to install by apt command.

```
$ sudo apt update
$ sudo apt install tzdiff
```

## Examples

In these examples, author's timezone is JST.

```
$ tzdiff America/Los_Angeles
Los_Angeles
2023-06-13 21:08 PDT   2023-06-14 13:08 JST
2023-06-13 22:08 PDT   2023-06-14 14:08 JST
2023-06-13 23:08 PDT   2023-06-14 15:08 JST
2023-06-14 00:08 PDT   2023-06-14 16:08 JST
2023-06-14 01:08 PDT   2023-06-14 17:08 JST
2023-06-14 02:08 PDT   2023-06-14 18:08 JST
2023-06-14 03:08 PDT   2023-06-14 19:08 JST
2023-06-14 04:08 PDT   2023-06-14 20:08 JST
2023-06-14 05:08 PDT   2023-06-14 21:08 JST
2023-06-14 06:08 PDT   2023-06-14 22:08 JST
```

Tzdiff supports TIMEZONE's completion. tzdiff looks for timezone information in "/usr/share/zoneinfo". For example,

```
$ tzdiff Lon                                 # enter RETURN instead of TAB
Arctic/Longyearbyen     Europe/London

$ tzdiff Lond
London
2023-06-14 05:13 BST   2023-06-14 13:13 JST
2023-06-14 06:13 BST   2023-06-14 14:13 JST
2023-06-14 07:13 BST   2023-06-14 15:13 JST
2023-06-14 08:13 BST   2023-06-14 16:13 JST
2023-06-14 09:13 BST   2023-06-14 17:13 JST
2023-06-14 10:13 BST   2023-06-14 18:13 JST
2023-06-14 11:13 BST   2023-06-14 19:13 JST
2023-06-14 12:13 BST   2023-06-14 20:13 JST
2023-06-14 13:13 BST   2023-06-14 21:13 JST
2023-06-14 14:13 BST   2023-06-14 22:13 JST

$ tzdiff New_ 0 5
New_York
2023-06-14 00:00 EDT   2023-06-14 13:00 JST
2023-06-14 01:00 EDT   2023-06-14 14:00 JST
2023-06-14 02:00 EDT   2023-06-14 15:00 JST
2023-06-14 03:00 EDT   2023-06-14 16:00 JST
2023-06-14 04:00 EDT   2023-06-14 17:00 JST
```

It is easy to check changes from daylight saving time to standard time

```
$ tzdiff -t 2017-11-05T11:00 Los New_ Brus
Los_Angeles            New_York               Brussels
2017-11-04 19:00 PDT   2017-11-04 22:00 EDT   2017-11-05 03:00 CET   2017-11-05 11:00 JST
2017-11-04 20:00 PDT   2017-11-04 23:00 EDT   2017-11-05 04:00 CET   2017-11-05 12:00 JST
2017-11-04 21:00 PDT   2017-11-05 00:00 EDT   2017-11-05 05:00 CET   2017-11-05 13:00 JST
2017-11-04 22:00 PDT   2017-11-05 01:00 EDT   2017-11-05 06:00 CET   2017-11-05 14:00 JST
2017-11-04 23:00 PDT   2017-11-05 01:00 EST   2017-11-05 07:00 CET   2017-11-05 15:00 JST
2017-11-05 00:00 PDT   2017-11-05 02:00 EST   2017-11-05 08:00 CET   2017-11-05 16:00 JST
2017-11-05 01:00 PDT   2017-11-05 03:00 EST   2017-11-05 09:00 CET   2017-11-05 17:00 JST
2017-11-05 01:00 PST   2017-11-05 04:00 EST   2017-11-05 10:00 CET   2017-11-05 18:00 JST
2017-11-05 02:00 PST   2017-11-05 05:00 EST   2017-11-05 11:00 CET   2017-11-05 19:00 JST
2017-11-05 03:00 PST   2017-11-05 06:00 EST   2017-11-05 12:00 CET   2017-11-05 20:00 JST
```

Specifying "0" and "24" at the end is convenient when you want to know what time 19:00 is your time in a foreign country.

```
$ tzdiff Brus 24 0
Brussels
2023-06-14 06:00 CEST   2023-06-14 13:00 JST
2023-06-14 07:00 CEST   2023-06-14 14:00 JST
2023-06-14 08:00 CEST   2023-06-14 15:00 JST
2023-06-14 09:00 CEST   2023-06-14 16:00 JST
2023-06-14 10:00 CEST   2023-06-14 17:00 JST
2023-06-14 11:00 CEST   2023-06-14 18:00 JST
2023-06-14 12:00 CEST   2023-06-14 19:00 JST
2023-06-14 13:00 CEST   2023-06-14 20:00 JST
2023-06-14 14:00 CEST   2023-06-14 21:00 JST
2023-06-14 15:00 CEST   2023-06-14 22:00 JST
2023-06-14 16:00 CEST   2023-06-14 23:00 JST
2023-06-14 17:00 CEST   2023-06-15 00:00 JST
2023-06-14 18:00 CEST   2023-06-15 01:00 JST
2023-06-14 19:00 CEST   2023-06-15 02:00 JST     <= This is your answer
2023-06-14 20:00 CEST   2023-06-15 03:00 JST
2023-06-14 21:00 CEST   2023-06-15 04:00 JST
2023-06-14 22:00 CEST   2023-06-15 05:00 JST
2023-06-14 23:00 CEST   2023-06-15 06:00 JST
2023-06-15 00:00 CEST   2023-06-15 07:00 JST
2023-06-15 01:00 CEST   2023-06-15 08:00 JST
2023-06-15 02:00 CEST   2023-06-15 09:00 JST
2023-06-15 03:00 CEST   2023-06-15 10:00 JST
2023-06-15 04:00 CEST   2023-06-15 11:00 JST
2023-06-15 05:00 CEST   2023-06-15 12:00 JST
```

## Platform

Tzdiff works with the following operating systems.

* macOS / FreeBSD / NetBSD / OpenBSD (It may work on DragonFly BSD.)
* Debian / Ubuntu / CentOS and many Linux distros
* Windows subsystem for Linux
