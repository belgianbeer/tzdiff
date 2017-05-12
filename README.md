# timediff
Show Time difference with local time in CLI (shell script)

*Usage*
    timediff [-0] [-n count] [-f format] [-t time] timezone [timezone ...]

Timediff with no arguments will display list of timezones.
Timediff with timezone will display the time differnces of remote time with local time.

For Example

    $ timediff America/Los_Angeles
    America/Los_Angeles
    2017-05-12 05:55 PDT	2017-05-12 21:55 JST
    2017-05-12 06:55 PDT	2017-05-12 22:55 JST
    2017-05-12 07:55 PDT	2017-05-12 23:55 JST
    2017-05-12 08:55 PDT	2017-05-13 00:55 JST
    2017-05-12 09:55 PDT	2017-05-13 01:55 JST
    2017-05-12 10:55 PDT	2017-05-13 02:55 JST
    2017-05-12 11:55 PDT	2017-05-13 03:55 JST
    2017-05-12 12:55 PDT	2017-05-13 04:55 JST
    2017-05-12 13:55 PDT	2017-05-13 05:55 JST
    2017-05-12 14:55 PDT	2017-05-13 06:55 JST

    $ timediff -0 -n 5 America/Los_Angeles
    America/Los_Angeles
    2017-05-12 06:00 PDT	2017-05-12 22:00 JST
    2017-05-12 07:00 PDT	2017-05-12 23:00 JST
    2017-05-12 08:00 PDT	2017-05-13 00:00 JST
    2017-05-12 09:00 PDT	2017-05-13 01:00 JST
    2017-05-12 10:00 PDT	2017-05-13 02:00 JST

Timediff supports TIMEZONE's complition. For example,

    timediff Lon	(enter RETURN insted of TAB)
    timediff Lond
    timediff Asia
    timediff Ame

*Options*

* -0: adjust to just o'clock.
* -h: show usage
* -n count: repeat count hours.
* -t time: set the specific time instead of current time.
 YYYY-mm-ddTHH:MM or YYYYmmddTHHMM is ok.
 (NetBSD and OpenBSD do not work).
* -f format: set the output format. default is '%F %R %Z'.

Timediff works with the following operating systems.

* OS X / FreeBSD / NetBSD / OpenBSD (It may works on DragonFly BSD.)
* Debian / Ubuntu / CentOS (and many Linux Box)
* Bash on Windows
