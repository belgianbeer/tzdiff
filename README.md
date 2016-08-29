# timediff
Show Time difference with local time in CLI (shell script)

*Usage*

    timediff
    timediff TIMEZONE
    timediff TIMEZONE COUNT

Timediff with no arguments will display a list of time zone.
Timediff with TIMEZONE will display the time differnces of remote time with local time.
If the COUNT is given, timediff displays COUNT times.

Timediff supports complition of TIMEZONE. For example,

    timediff Tokyo 24
    timediff Asia/Tokyo
    timediff Lon
    timediff Lond
    timediff Asia
    timediff Ame

All above statement works fine.

Timediff works with the following operating systems.

* OS X / FreeBSD / NetBSD / OpenBSD (It may works on DragonFly BSD.)
* Debian / Ubuntu / CentOS (and many Linux Box)
* Bash on Windows
