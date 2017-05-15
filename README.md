# timediff
Show Time difference with local time in CLI (shell script)

*Usage*

    timediff [-0] [-n count] [-f format] [-t time] timezone [timezone ...]

Timediff with no arguments will display list of timezones.
Timediff with timezone will display the time differnces of remote time with local time.

*Options*

* -h: show usage
* -0: adjust to just o'clock.
* -n count: repeat count hours.
* -f format: set the output format. default is '%F %R %Z'.
* -t time: set the specific time instead of current time.
 'YYYY-mm-ddTHH:MM' or 'YYYYmmddTHHMM' is ok.

Timediff supports TIMEZONE's complition. For example,

    timediff Lon             # enter RETURN insted of TAB
    timediff Lond
    timediff Eur
    timediff Ame

*Example* (Author's local time is JST)

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

    $ timediff -0 -n 5 New_
    America/New_York
    2017-05-12 08:00 EDT    2017-05-12 21:00 JST
    2017-05-12 09:00 EDT    2017-05-12 22:00 JST
    2017-05-12 10:00 EDT    2017-05-12 23:00 JST
    2017-05-12 11:00 EDT    2017-05-13 00:00 JST
    2017-05-12 12:00 EDT    2017-05-13 01:00 JST

It is easy to check changes from daylight saving time to winter time.

    $ timediff  -t 2017-11-05T11:00 Los New_ Brus
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
