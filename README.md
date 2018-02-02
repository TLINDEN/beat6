## beat6 - a simple ipv6 http stress tester

This is a simple perl script to stress test http servers via ipv6 only.

### dependencies

Beat6 requires perl with thread support and the following modules:

* Net::HTTPS
* Net::DNS
* IO::Socket::SSL
* IO::Socket::INET6
* Time::HiRes
* Number::Bytes::Human

### install

I suggest using perlbrew. Sample installation:

    wget -O - https://install.perlbrew.pl | bash
    perlbrew install-cpanm
    perlbrew install --thread -n perl-5.22.4
    cpanm Net::HTTPS
    cpanm IO::Socket::INET6
    cpanm IO::Socket::SSL
    cpanm Number::Bytes::Human
    cpanm Net::DNS
    
Then execute beat6 with:

    perlbrew use perl-5.22.4
    perl beat6 -h

### usage

    Usage beat6 [-HpPfdrlcubtvh] [<host>]
    Options:
    --host      -H <host>    Hostname (must have an ipv6 dns entry)
    --port      -P <port>    TCP Port (default 443)
    --path      -p <uri>     Uri path on <host> to fetch
    --urlfile   -f <file>    File containing uri path's to fetch,
                             Format:
                                # comment
                                GET /path/to/html
                                POST /search string=foobar
                             Post data must be url-encoded
    --delay     -d <delay>   Delay between requests (default 0),
                             Set to range for random delays
    --repeats   -r <count>   How many <count> times shall we connect
                             (default 1, 0 = endless)
    --limit     -l <seconds> How many <seconds> shall we run, cannot
                             be mixed with --repeats, supported
                             abbrevs: m (minutes), h (hours), e.g.
                             --limit 10m or --limit 2h
    --clients   -c <count>   How many concurrent threads to use
    --useragent -u <str>     Set UserAgent to <str> (default Beat6/1)
    --bindaddr  -b <addr>    IPv6 address to use as source
    --header       <header>  Add <header> to requests (multiple ok)
    --timeout   -t <seconds> Set timeout to <seconds> (per session)
    --verbose   -v           Verbose output
    --help      -h -?        Help message
        
    This is beat6 verion 1, released under the terms of the GPLv3.

### license

GPLv3
