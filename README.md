Shellify
========

Turn a command into an interactive shell. This script is designed for use
within zsh, although it probably wouldn't be too hard to get it to support
bash, too. This was inspired by (this shellify
script)[https://github.com/clehner/shellify], but the code is very different
and they have different features.

Usage
-----

    shellify <command> [<prompt>]

Features
--------

 - If no prompt is given, uses a default prompt
 - Send SIGINT (Ctrl+C) to cancel a line and restart
 - Sources ~/.zshrc, if it exists, so you can use your aliases and settings
 - Begin a line with `!` to call an external command

Examples
-------

    $ shellify git
    git » sttus^C
    git » status
    On branch master
    nothing to commit, working directory clean
    git »
    $ shellify git '>>> '
    >>> status
    On branch master
    nothing to commit, working directory clean
    >>>
    $ echo "alias g=git" >> ~/.zshrc
    $ shellify g
    g » status
    On branch master
    nothing to commit, working directory clean
    g » !ls
    README.md
    g »
