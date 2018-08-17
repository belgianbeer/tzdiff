# timediff
Show Time differences with local time in CLI (shell script)

*Usage*

    timediff [-0] [-n count] [-f format] [-t time] timezone [timezone ...] [count] [0]

Timediff with no arguments will display list of timezones.
Timediff with timezone will display the time differnces of remote time with local time.

*Options*

* -h: show usage
* -0: round down to hour
* -n count: max hours (default: 10)
* -f format: output format (using '+output_fmt' of date(1))
* -t time: set the start time instead of current time.
 'YYYY-mm-ddTHH:MM' or 'YYYYmmddTHHMM' is ok.

*Example* (Author's time is JST)

    $ timediff
    Africa/         Australia/      Etc/            MST             WET
    America/        CET             Europe/         MST7MDT         posixrules
    Antarctica/     CST6CDT         Factory         PST8PDT         zone.tab
    Arctic/         EET             HST             Pacific/
    Asia/           EST             Indian/         SystemV/
    Atlantic/       EST5EDT         MET             UTC

    $ timediff America/Los_Angeles
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

Timediff supports TIMEZONE's complition. For example,

    $ timediff Lon             # enter RETURN insted of TAB
    Arctic/Longyearbyen     Europe/London

    $ timediff Lond
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

    $ timediff -0 -n 5 New_
    America/New_York
    2017-05-12 08:00 EDT    2017-05-12 21:00 JST
    2017-05-12 09:00 EDT    2017-05-12 22:00 JST
    2017-05-12 10:00 EDT    2017-05-12 23:00 JST
    2017-05-12 11:00 EDT    2017-05-13 00:00 JST
    2017-05-12 12:00 EDT    2017-05-13 01:00 JST

It is easy to check changes from daylight saving time to winter time.

    $ timediff -t 2017-11-05T11:00 Los New_ Brus
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

Timediff works with the following operating systems.

* OS X / FreeBSD / NetBSD / OpenBSD (It may work on DragonFly BSD.)
* Debian / Ubuntu / CentOS (and many Linux Box)
* Bash on Windows
