# docker-irccat

irccat is an IRC bot that simplifies posting to IRC from shell scripts.
This is a [docker](https://www.docker.io) image that eases setup of the python port of irccat.

## Usage

First, create a configuration directory on your host :

```
$ mkdir /opt/irccat/config
```

Write into this directory the config file `irccat.ini` similar to this sample :

    [server]
    address = example.com
    port = 6667
    password=

    [bot]
    nick = irccat
    messagedelay = 250

    [cat]
    ip = 0.0.0.0
    port = 5000

    [channel_log]
    default = true
    name = #test

    [channel_test]
    name = #log

Finally, run a new container using this image :

```
$ docker run -it --name irccat -v /opt/irccat/config:/opt/irccat/config plewin/irccat
```

You can now post to IRC any command line output by piping to the new container's port using netcat.
