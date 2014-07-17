#bob

bob is a command-line client for managing dokku applications.
It is a very thin client, defining no local commands and instead
passing them on to the dokku server.

##Installation
Just put the bob and shflags executables anywhere in your $PATH, such as ~/bin.
bob comes with its own copy of shflags to parse the arguments. If you already have that installed somewhere, you don't shflags.

##Requirements
Bob needs the following to work:
    - git (>=1.7.5)
    - A remote named `dokku` setup in your git

##Working
Bob reads the dokku remote using git, parses it to get the dokku hostname (and username) and appname. Then any commands are passed to the dokku server with the correct appname.

##Commands
The following two commands are equivalent:

    ssh dokku@server <command> app [args]
    bob <command> [args]

For eg to add a config option to your dokku application, just run:

    bob config:set VAR1=hello VAR2=world

To see a full list of available commands, just run `bob help`, which is actually equivalent to `ssh dokku@server help`