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

macOS tools:

* [Homebrew] for managing operating system libraries
* [Homebrew Cask] for managing Mac applications distributed as binaries from the CLI

[Homebrew]: http://brew.sh/
[Homebrew Cask]: http://caskroom.io/

Unix tools:

* [Bash Completion] for typing faster
* [Term] for controlling tabs from the command line
* [Git] for version control
* [OpenSSL] for Transport Layer Security (TLS)
* [LibYAML] is a YAML 1.1 parser and emitter needed by Ruby
* [Watchman] for watching for filesystem events

[Bash Completion]: http://bash-completion.alioth.debian.org/
[Term]: https://github.com/liyanage/macosx-shell-scripts/blob/master/term
[Git]: https://git-scm.com/
[OpenSSL]: https://www.openssl.org/
[LibYAML]: https://pyyaml.org/wiki/LibYAML
[Watchman]: https://facebook.github.io/watchman/

Heroku tools:

* [Heroku Toolbelt] for interacting with the Heroku API

[Heroku Toolbelt]: https://toolbelt.heroku.com/

Programming languages, package managers, and configuration:

* [Bundler] for managing Ruby libraries
* [Ruby] stable for writing general-purpose code
* [RVM] for managing Ruby environments
* [NVM] for running apps and installing JavaScript packages
* [Saas] for writing useful CSS
* [Yarn] is a package manager

[Bundler]: http://bundler.io/
[Ruby]: https://www.ruby-lang.org/en/
[RVM]: https://rvm.io/
[NVM]: https://github.com/creationix/nvm/
[Saas]: http://sass-lang.com/
[Yarn]: https://yarnpkg.com/en/

Databases:

* [Postgres] for storing relational data
* [MongoDB] for storing document-oriented data

[Postgres]: http://www.postgresql.org/
[MongoDB]: https://www.mongodb.com/

Other tools:

* [Sublime] for editing text in a nice way

[Sublime]: http://www.sublimetext.com/

It should take less than 15 minutes to install (depends on your machine).

Customize in `~/.laptop.local`
------------------------------

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.

For example:

```sh

#!/bin/sh

brew_cask_install_or_upgrade 'spectacle'
brew_cask_install_or_upgrade 'slack'
brew_cask_install_or_upgrade 'sourcetree'
brew_cask_install_or_upgrade 'skitch'
brew_cask_install_or_upgrade 'sketch'
brew_cask_install_or_upgrade 'mamp'
brew_cask_install_or_upgrade 'keepassx'
brew_cask_install_or_upgrade 'filezilla'
brew_cask_install_or_upgrade 'balsamiq-mockups'
brew_cask_install_or_upgrade 'pandora'
brew_cask_install_or_upgrade 'amazon-music'
brew_cask_install_or_upgrade 'spotify'
brew_cask_install_or_upgrade 'kindle'
brew_cask_install_or_upgrade 'dropbox'
brew_cask_install_or_upgrade 'android-file-transfer'
brew_cask_install_or_upgrade 'vlc'
brew_cask_install_or_upgrade 'muzzle'

```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

Laptop functions such as `fancy_echo`,
`brew_install_or_upgrade`, `brew_cask_install_or_upgrade`, and
`gem_install_or_update`
can be used in your `~/.laptop.local`.
