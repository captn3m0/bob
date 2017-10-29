# bob

bob is a command-line client for managing dokku applications.
It is a very thin client, defining no local commands and instead
passing them on to the dokku server.

## Installation
Just put the bob executable anywhere in your $PATH, such as ~/bin.

## Requirements
Bob needs the following to work:

    - git (>=1.7.5)
    - A remote named `dokku` setup in your git config

## Working
Bob reads the dokku remote using git, parses it to get the dokku hostname (and username) and appname. Then any commands are passed to the dokku server with the correct appname. *Note*: This may result in some invalid commands. 

## Commands
The following two commands are equivalent:

    ssh dokku@server <command> app [args]
    bob <command> [args]

For eg to add a config option to your dokku application, just run:

    bob config:set VAR1=hello VAR2=world

To see a full list of available commands, just run `bob help`, which is actually equivalent to `ssh dokku@server help <app>`. 

**Note**: Since bob is just a thin client, it has no way of differentiating between various kinds of dokku commands, and the [app] parameter is always sent to the server as the second argument. This means that not all commands are compatible with bob.

## Valid commands

This is a list of commands known to work with bob (Basically those where the first argument is <app> or if the command accepts no arguments).

    config                                    display the config vars for current app
    config:get KEY                            display a config value for current app
    config:set KEY1=VALUE1 [KEY2=VALUE2 ...]  set one or more config vars
    config:unset KEY1 [KEY2 ...]              unset one or more config vars
    delete                                    Delete current application
    help                                      Print the list of commands
    link                                      display links for current app
    link:create NAME [ALIAS]                  create a link for current app
    link:delete NAME [ALIAS]                  delete a link for current app
    logs [-t]                                 Show the last logs for current application (-t follows)
    plugins-install                           Install active plugins
    plugins                                   Print active plugins
    postgresql:link <db>                      Link current app to a PostgreSQL database
    postgresql:list                           Display list of PostgreSQL containers
    redis:create                              Create a Redis container
    redis:delete                              Delete specified Redis container
    redis:info                                Display container informations
    redis:link <container>                    Link current app to a Redis container
    redis:logs                                Display last logs from Redis container
    run <cmd>                                 Run a command in the environment of current application
    url                                       Show the URL for current application
    version                                   Print dokku's version

## Licence
bob is licenced under the [MIT Licence](http://nemo.mit-license.org).
