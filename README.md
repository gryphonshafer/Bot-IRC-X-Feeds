# NAME

Bot::IRC::X::Feeds - Bot::IRC plugin to watch and notify on changes in RSS feeds

# VERSION

version 1.02

[![Build Status](https://travis-ci.org/gryphonshafer/Bot-IRC-X-Feeds.svg)](https://travis-ci.org/gryphonshafer/Bot-IRC-X-Feeds)
[![Coverage Status](https://coveralls.io/repos/gryphonshafer/Bot-IRC-X-Feeds/badge.png)](https://coveralls.io/r/gryphonshafer/Bot-IRC-X-Feeds)

# SYNOPSIS

    use Bot::IRC;

    Bot::IRC->new(
        connect => { server => 'irc.perl.org' },
        plugins => ['Feeds'],
        vars    => {
            x-feeds => {
                interval        => 10,
                max_per         => 5,
                fresh_intervals => 2,
            }
        },
    )->run;

# DESCRIPTION

This [Bot::IRC](https://metacpan.org/pod/Bot::IRC) plugin adds functionality so bots can watch and notify on
changes in RSS feeds. You can tell the bot to start following feeds.

    bot feed add URL [FORUMS]

You can optionally provide a "FORUMS" string, which is a list of channels the
bot should report on for the feed. By default, the bot reports on all channels
it has joined. (Requires the [Bot::IRC::Join](https://metacpan.org/pod/Bot::IRC::Join) plugin.) The list of channels
must be comma-delimited with no spaces.

You can list the feeds the bot is following:

    bot feed list

And you can remove feeds from being watched:

    bot feed remove URL

You can also remove all feeds from being watched:

    bot feed remove all

## Configuration Settings

Setting the `x-feeds` values allows for configuration.

    Bot::IRC->new(
        connect => { server => 'irc.perl.org' },
        plugins => ['Feeds'],
        vars    => {
            x-feeds => {
                interval        => 10,
                max_per         => 5,
                fresh_intervals => 2,
            }
        },
    )->run;

The "interval" value is the time interval between calls to feeds, measured in
minutes.

The "max\_per" value is the number of items returned per feed per call.

The "fresh\_intervals" setting means how many intervals of time backward should
items be considered fresh enough to report on. For example, if you set an
interval of 5 minutes and a fresh\_intervals of 3, then any item in a feed with
a publication time older than 15 will not be reported.

The default values for all are shown in the example above.

# SEE ALSO

You can look for additional information at:

- [Bot::IRC](https://metacpan.org/pod/Bot::IRC)
- [GitHub](https://github.com/gryphonshafer/Bot-IRC-X-Feeds)
- [CPAN](http://search.cpan.org/dist/Bot-IRC-X-Feeds)
- [MetaCPAN](https://metacpan.org/pod/Bot::IRC::X::Feeds)
- [AnnoCPAN](http://annocpan.org/dist/Bot-IRC-X-Feeds)
- [Travis CI](https://travis-ci.org/gryphonshafer/Bot-IRC-X-Feeds)
- [Coveralls](https://coveralls.io/r/gryphonshafer/Bot-IRC-X-Feeds)
- [CPANTS](http://cpants.cpanauthors.org/dist/Bot-IRC-X-Feeds)
- [CPAN Testers](http://www.cpantesters.org/distro/T/Bot-IRC-X-Feeds.html)

# AUTHOR

Gryphon Shafer <gryphon@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2016 by Gryphon Shafer.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
