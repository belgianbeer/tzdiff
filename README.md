# timediff
Show Time difference with local time in CLI (shell script)

*Usage*

    timediff
    timediff TIMEZONE
    timediff TIMEZONE COUNT
    timediff TIMEZONE COUNT 0
    timediff TIMEZONE COUNT 0
    timediff TIMEZONE 0

Timediff with no arguments will display a list of time zone.
Timediff with TIMEZONE will display the time differnces of remote time with local time.
If the COUNT is given, timediff displays COUNT times (default is 10).
If 0 is given on count then the time adjust to just oclock.

Timediff supports complition of TIMEZONE. For example,

    timediff Tokyo 24
    timediff Asia/Tokyo
    timediff Lon	(enter RETURN insted of TAB)
    timediff Lond
    timediff Asia
    timediff Ame

All above statement works fine.

2017-05-17
Timediff supports multiple timezones.

Timediff works with the following operating systems.

* OS X / FreeBSD / NetBSD / OpenBSD (It may works on DragonFly BSD.)
* Debian / Ubuntu / CentOS (and many Linux Box)
* Bash on Windows
