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
* [Subversion] for more version control
* [OpenSSL] for Transport Layer Security (TLS)
* [Watchman] for watching for filesystem events

[Bash Completion]: http://bash-completion.alioth.debian.org/
[Term]: https://github.com/liyanage/macosx-shell-scripts/blob/master/term
[Git]: https://git-scm.com/
[Subversion]: https://subversion.apache.org/
[OpenSSL]: https://www.openssl.org/
[Watchman]: https://facebook.github.io/watchman/

Heroku tools:

* [Heroku CLI] for interacting with the Heroku API

[Heroku CLI]: https://devcenter.heroku.com/articles/heroku-cli

Programming languages, package managers, and configuration:

* [LibYAML] is a YAML 1.1 parser and emitter needed by Ruby
* [Yarn] is a package manager
* [NVM] for running apps and installing JavaScript packages
* [Java 8] for running big ol' Java apps
* [Maven] for build automation
* [Ant] to help build Java applications
* [Bundler] for managing Ruby libraries
* [Ruby] stable for writing general-purpose code
* [RVM] for managing Ruby environments
* [Saas] for writing useful CSS

[LibYAML]: https://pyyaml.org/wiki/LibYAML
[Yarn]: https://yarnpkg.com/en/
[NVM]: https://github.com/creationix/nvm/
[Java 8]: http://www.oracle.com/technetwork/java/javase/jdk-8-readme-2095712.html
[Maven]: http://maven.apache.org/
[Ant]: http://ant.apache.org/
[Bundler]: http://bundler.io/
[Ruby]: https://www.ruby-lang.org/en/
[RVM]: https://rvm.io/
[Saas]: http://sass-lang.com/

Servers:

* [Tomcat 8] is a "pure Java" HTTP web server environment in which Java code can run.

[Tomcat 8]: https://tomcat.apache.org/

Databases:

* [Postgres] for storing relational data
* [MongoDB] for storing document-oriented data
* [Elasticsearch] for RESTful search and analytics

[Postgres]: http://www.postgresql.org/
[MongoDB]: https://www.mongodb.com/
[Elasticsearch]: https://www.elastic.co/products/elasticsearch

It should take less than 15 minutes to install (depends on your machine).

Customize in `~/.laptop.local`
------------------------------

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.

For example:

```sh

#!/bin/sh

brew bundle --file=- <<EOF
cask "sublime-text"
cask "spectacle"
cask "slack"
cask "sourcetree"
cask "skitch"
cask "sketch"
cask "cyberduck"
cask "balsamiq-mockups"
cask "spotify"
cask "android-file-transfer"
cask "onedrive"
EOF

```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

Laptop functions such as `fancy_echo` and `gem_install_or_update`
can be used in your `~/.laptop.local`.
