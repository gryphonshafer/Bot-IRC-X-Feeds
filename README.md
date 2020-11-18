# NAME

Bot::IRC::X::Feeds - Bot::IRC plugin to watch and notify on changes in RSS feeds

# VERSION

version 1.05

[![test](https://github.com/gryphonshafer/Bot-IRC-X-Feeds/workflows/test/badge.svg)](https://github.com/gryphonshafer/Bot-IRC-X-Feeds/actions?query=workflow%3Atest)
[![codecov](https://codecov.io/gh/gryphonshafer/Bot-IRC-X-Feeds/graph/badge.svg)](https://codecov.io/gh/gryphonshafer/Bot-IRC-X-Feeds)

# SYNOPSIS

    use Bot::IRC;

    Bot::IRC->new(
        connect => { server => 'irc.perl.org' },
        plugins => ['Feeds'],
        vars    => {
            'x-feeds' => {
                interval => 10,
                max_per  => 5,
            }
        },
    )->run;

# DESCRIPTION

This [Bot::IRC](https://metacpan.org/pod/Bot%3A%3AIRC) plugin adds functionality so bots can watch and notify on
changes in RSS feeds. You can tell the bot to start following feeds.

    bot feed add URL [FORUMS]

You can optionally provide a "FORUMS" string, which is a list of channels the
bot should report on for the feed. By default, the bot reports on all channels
it has joined. (Requires the [Bot::IRC::Join](https://metacpan.org/pod/Bot%3A%3AIRC%3A%3AJoin) plugin.) The list of channels
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
            'x-feeds' => {
                interval => 10,
                max_per  => 5,
            }
        },
    )->run;

The "interval" value is the time interval between calls to feeds, measured in
minutes.

The "max\_per" value is the number of items returned per feed per call.

The default values for all are shown in the example above.

# SEE ALSO

You can look for additional information at:

- [Bot::IRC](https://metacpan.org/pod/Bot%3A%3AIRC)
- [GitHub](https://github.com/gryphonshafer/Bot-IRC-X-Feeds)
- [MetaCPAN](https://metacpan.org/pod/Bot::IRC::X::Feeds)
- [GitHub Actions](https://github.com/gryphonshafer/Bot-IRC-X-Feeds/actions)
- [Codecov](https://codecov.io/gh/gryphonshafer/Bot-IRC-X-Feeds)
- [CPANTS](http://cpants.cpanauthors.org/dist/Bot-IRC-X-Feeds)
- [CPAN Testers](http://www.cpantesters.org/distro/T/Bot-IRC-X-Feeds.html)

# AUTHOR

Gryphon Shafer <gryphon@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2021 by Gryphon Shafer.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
