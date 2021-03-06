# terraria

Docker images to run a Terraria Server. Images with [TShock Server](https://github.com/Pryaxis/TShock) or [Vanilla Server](https://terraria.gamepedia.com/Server) are available.


![Docker Image Size (tag)](https://img.shields.io/docker/image-size/daninfuchs/terraria-server/latest) ![MicroBadger Layers (tag)](https://img.shields.io/microbadger/layers/daninfuchs/terraria-server/latest) [![Docker Pulls](https://img.shields.io/docker/pulls/daninfuchs/terraria-server.svg)]() [![Docker Stars](https://img.shields.io/docker/stars/daninfuchs/terraria-server.svg)]()

Shamelessly forked by DaninFuchs to add working password support for the super-well-known bug of configured passwords not applying on startup of the vanilla server because it's KIND OF IMPORTANT TO HAVE WORKING. The 'password' environment variable will be passed, clear-text, to the server binary on execution. Anyone with access to process listing capability on your server (pretty much everyone) can see this in clear-text, it is not 'secure' by any means. I run this on my personal hardware, I might add more features if I find them missing, good luck because It Works For Me(tm). YMMV.

NOTICE: Terraria 1.4 is now avaiable for the Vanilla Server and TShock has a pre-release version out for it as well. Keep in mind the pre-release will have bugs. For more infomation about the Tshock pre-release check there [repo website](https://github.com/Pryaxis/TShock#readme).

### Usage
```
docker create --rm -it \
  --name=terraria \
  -v <path to data>:/config \
  -e world=<world_file_name> \
  -e password=<plaintext_password> \
  -p 7777:7777 \
  daninfuchs/terraria-server
```

Docker Images are avaiable on [Docker Hub](https://hub.docker.com/r/daninfuchs/terraria-server)

### Supported tags and respective `Dockerfile` links
* vanilla-1.4.1.1, vanilla-latest, latest [(containers/vanilla/1.4.1.1/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/vanilla/1.4.1.1/Dockerfile)
* vanilla-1.4.0.5 [(containers/vanilla/1.4.0.5/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/vanilla/1.4.0.5/Dockerfile)
* vanilla-1.3.5.3 [(containers/vanilla/1.3.5.3/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/vanilla/1.3.5.3/Dockerfile)
* vanilla-1.3.4.4 [(containers/vanilla/1.3.4.4/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/vanilla/1.3.4.4/Dockerfile)
* vanilla-1.3.3.3 [(containers/vanilla/1.3.3.3/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/vanilla/1.3.3.3/Dockerfile)
* vanilla-1.3.2.1 [(containers/vanilla/1.3.2.1/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/vanilla/1.3.2.1/Dockerfile)
* tshock-4.40-pre13, tshock-latest [(containers/tshock/4.40-pre13/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock/4.40-pre13/Dockerfile)
* tshock-4.3.26 [(containers/tshock/4.3.26/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock/4.3.26/Dockerfile)
* tshock-4.3.25 [(containers/tshock/4.3.25/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock/4.3.25/Dockerfile)
* tshock-4.3.24 [(containers/tshock/4.3.24/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock/4.3.24/Dockerfile)
* tshock-4.3.23 [(containers/tshock/4.3.23/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock/4.3.23/Dockerfile)
* tshock-dev-1595, tshock-dev-latest [(containers/tshock-dev/1595/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock-dev/1595/Dockerfile)
* tshock-dev-1594 [(containers/tshock-dev/1594/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock-dev/1594/Dockerfile)
* tshock-dev-1593 [(containers/tshock-dev/1593/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock-dev/1593/Dockerfile)
* tshock-dev-1592 [(containers/tshock-dev/1592/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock-dev/1592/Dockerfile)
* tshock-dev-1591 [(containers/tshock-dev/1591/Dockerfile)](https://github.com/daninfuchs/terraria-server/blob/master/containers/tshock-dev/1591/Dockerfile)

### Quick reference
- Where to get help:\
The [TShock Discussions](https://github.com/Pryaxis/TShock/discussions) or the [Terraria Forum](https://forums.terraria.org/index.php?forums/)

- Where to file issues:\
https://github.com/daninfuchs/terraria-server/issues

- Supported Docker versions:\
[We support the latest release](https://github.com/docker/docker-ce/releases/latest) (down to 1.8 on a best-effort basis)

### What is Terraria Server?
A Terraria server provides a platform for players to connect over the internet or other network for multiplayer games of [Terraria](https://terraria.org/).

## How to use

### Generating a new world
To run with out user intervention Terraria Server needs to be configure to use an already generated world. This means you can use one that you have already generated or you can generate one via docker by running this command:
```
sudo docker run --rm -it \
    -v $HOME/terraria/config:/config \
    --name=terraria \
    daninfuchs/terraria-server
```
You can then follow the prompts to create a new world.

### Starting your server with a preexisting world
The world file needs to exist in the config folder.
To start a server using an already generated world, use this command:
```
sudo docker run --rm -dit \
  --name=terraria \
  -v $HOME/terraria/config:/config \
  -e world=<world_file_name> \
  -e password=<plaintext_password> \
  -p 7777:7777 \
  daninfuchs/terraria-server
```

If you get an error from docker saying the container name already exists, it means you need to remove your old docker container process.
`sudo docker rm terraria`

If you want to reattach to any running containers:
`sudo docker attach terraria`
Now you can execute any commands to the terraria server. Ctrl-p Ctrl-q will detatch you from the process.

### Example Docker Compose file
Here is an example docker-compose file that enables to the use of the vanilla server
```
version: '3'

services:
  terraria:
    image: daninfuchs/terraria-server:vanilla-latest
    ports:
      - '7777:7777'
    restart: unless-stopped
    environment:
      - world=<world_file_name>
      - password=<plaintext_password>
    volumes:
      - $HOME/terraria/config:/config
    tty: true
    stdin_open: true
```

### daninfuchs/terraria-server:tshock-latest
TShock is a server modification for Terraria, written in C#, and based upon the Terraria Server API. It uses JSON for configuration management, and offers several features not present in the Terraria Server normally.

### daninfuchs/terraria-server:tshock-dev-latest
TShock dev are unreleased development builds of TShock. These builds may be unstable but they are updated faster then the released versions so they support new versions of Terraria faster.

### daninfuchs/terraria-server:vanilla-latest
Vanilla Terraria server is the server software provided by the developers of Terraria. This version has only basic features but it is updated along with the main game so it should always be up to date.

If a docker image isn't available of the latest versions please [contact us](https://www.bearded.io/#footer) about the new release so we can update this repo.

### FAQ
- Can I manage my own plugins for tshock?\
Yes, if you want manage you own plugins for tshock containers, you can add a volume mount to your docker command via `-v <path to plugins folder>:/tshock/ServerPlugins`. If you want to maintain any of the plugins that ship with tshock, you will need to copy them into the ServerPlugins folder. Mounting the plugins folder will override the plugins that ship with tshock.
- I started the container but it keeps asking me to select a world, help?!\
You need to ether start the server with an existing world, in which case the server will start automaticly. Or you need to run the continer interactivly using the -it flag. This will allow you to create a new world.
-The server returns a "System.NullReferenceException" exception when loading a world. Help!\
The server requires a tty connection, so when starting the server via docker run make sure to include the -it flag. Or if running using docker-compose make sure to add tty: true (see this [issue](https://github.com/daninfuchs/terraria-server/issues/7))

#### *Notes*
* Please check the [TShock instructions](https://tshock.readme.io/docs/getting-started) for properly installing and configuring your terraria server.
* Any [additional command-line instructions](https://tshock.readme.io/docs/command-line-parameters) can be added to the end of either method for launching a server.  Docker maps the $HOME/terraria/world linux-host folder to the /tshock/world container-folder.
* More information about running a server is available in the [wiki](https://terraria.gamepedia.com/Server).

#### License

The MIT License (MIT)
Copyright (c) 2020 Brandon Skrtich
