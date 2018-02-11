# Docker Container for Lightning Network Daemon

This is a simple, containerized way to easily run the Lightning Network Daemon.

This is based on the [official community installation guide](http://dev.lightning.community/guides/installation/).

## Requirements

[Docker](https://docs.docker.com/engine/installation/)

## How do I run it? 

You can pull from [this Docker repo](https://hub.docker.com/r/samjhill/lnd-docker/)

OR run manually:

First, clone this repo. Then, from inside the newly-cloned folder:

1) `docker build -t lnd .` 

2) `docker run -it --rm --name my-lnd lnd`

3) Let this run; wait for the testnet blockchain to sync. It could take a while (~40gb to download as of writing)

4) Enter the Docker container in a new window: `docker exec -it my-lnd bash`

5) Start lnd: `lnd --bitcoin.active --bitcoin.testnet --debuglevel=debug --bitcoin.rpcuser=kek --bitcoin.rpcpass=kek` (include `--externalip=X.X.X.X`) if you want this to be public-facing
