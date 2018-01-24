Laptop
======

Laptop is a script to set up an OS X laptop for web development. It's based on what [thoughtbot did here](https://github.com/thoughtbot/laptop).

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages
based on what is already installed on the machine.

Requirements
------------

I've tested this on:

* macOS Sierra (10.12)

Older versions may work but aren't regularly tested. 

Install
-------

Download, review, then execute the script:

```sh
curl --remote-name https://raw.githubusercontent.com/dpardes/laptop/master/mac
less mac
sh mac 2>&1 | tee ~/laptop.log
```

Debugging
---------

Your last Laptop run will be saved to `~/laptop.log`.
Read through it to see if you can debug the issue yourself.
If not, let me know; I might be able to help.

What it sets up
---------------

* [Homebrew] for managing operating system libraries
* [Bash Completion] for typing faster
* [Term] for controlling tabs from the command line
* [Git] for version control
* [Heroku Toolbelt] for interacting with the Heroku API
* [Postgres] for storing relational data
* [Redis] for storing key-value data
* [MongoDB] for storing document-oriented data
* [NVM] for running apps and installing JavaScript packages
* [Grunt] for automating JavaScript tasks
* [Grunt Express Server] for runing an Express Server via Grunt
* [RVM] for managing Ruby environments
* [Ruby] stable for writing general-purpose code
* [Bundler] for managing Ruby libraries
* [Foreman] for managing web processes
* [Homebrew Cask] for managing Mac applications distributed as binaries from the CLI
* [Sublime] for editing text in a nice way

[Homebrew]: http://brew.sh/
[Bash Completion]: http://bash-completion.alioth.debian.org/
[Term]: https://github.com/liyanage/macosx-shell-scripts/blob/master/term
[Git]: https://git-scm.com/
[Foreman]: https://github.com/ddollar/foreman
[Homebres Cask]: http://caskroom.io/
[Heroku Toolbelt]: https://toolbelt.heroku.com/
[RVM]: https://rvm.io/
[Bundler]: http://bundler.io/
[NVM]: https://github.com/creationix/nvm/
[Grunt]: http://gruntjs.com/
[Grunt Express Server]: https://github.com/ericclemmons/grunt-express-server/
[Postgres]: http://www.postgresql.org/
[Redis]: http://redis.io/
[MongoDB]: https://www.mongodb.com/
[Ruby]: https://www.ruby-lang.org/en/
[Homebrew Cask]: http://caskroom.io/
[Sublime]: http://www.sublimetext.com/

It should take less than 15 minutes to install (depends on your machine).

Customize in `~/.laptop.local`
------------------------------

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.

For example:

```sh

#!/bin/sh

brew_cask_install_or_upgrade 'keepassx'
brew_cask_install_or_upgrade 'filezilla'
brew_cask_install_or_upgrade 'balsamiq-mockups'
brew_cask_install_or_upgrade 'pandora'
brew_cask_install_or_upgrade 'amazon-music'
brew_cask_install_or_upgrade 'kindle'
brew_cask_install_or_upgrade 'slack'
brew_cask_install_or_upgrade 'dropbox'
brew_cask_install_or_upgrade 'google-chrome'

```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

Laptop functions such as `fancy_echo`,
`brew_install_or_upgrade`, `brew_cask_install_or_upgrade`, and
`gem_install_or_update`
can be used in your `~/.laptop.local`.
