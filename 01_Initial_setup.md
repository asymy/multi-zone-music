# Music Server

The music server is running mopidy and shairport-sync. Mopidy is a musc server software and can accept inputs from various sources through add ons and then send the result to a pipe output. Shairport-sync is an open source implimentation of airplay (audio only) and can also output to a pipe. The pipe output can be fed into snap-server which is the server component of snapcast a multizone audio handler.
The server can be run as a VM (in my case) or on a raspberry pi which could also be running as a player (although I would say a R-pi 3 and up would be reccommended for better performance).

## Running on ubuntu server 20.04

- Tested on 20.04 and raspberry pi 4 running rasbian lite
- Install your OS
- Update and upgrade your packages and then install packages we need for later

```bash

sudo apt update && sudo apt upgrade -y
sudo apt install -y git python3-pip

```

# Raspberry pi

The raspberry pi is running only snapcast client. The snapserver sends the music over the network to the client. The clients are autodiscovered and are handled gracefully when they go offline.

- Flash the sd card with raspian lite
- Make sure you can access by ssh
- Boot up raspberry pi

```bash

sudo apt update && sudo apt upgrade -y
sudo raspi-config

```

- Reset the password, make sure the audio output is set right and reallocate the disk space
- Reboot the ras-pi