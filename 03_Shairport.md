# Shairport-sync

- Resources:
  - https://github.com/mikebrady/shairport-sync
  - https://github.com/mikebrady/shairport-sync/blob/master/INSTALL.md
  - https://github.com/badaix/snapcast/blob/master/doc/player_setup.md#airplay
- I found the recomended way of integration to be difficult so instead we will set up shairport to output to a pipe just like mopidy

## Install 

```bash

sudo apt-get install shairport-sync
sudo nano /etc/shairport-sync.conf

```

## Configure

- Edit your shairport-sync configuration file to have the following lines added

```config
general =
{
    name = "Your name here";
    output_backend = "pipe";
};
pipe =
{
	name = "/tmp/snapfifo-airplay"; // there is no default pipe name for the output
};

```
```bash

# Handy comands for shairport
sudo systemctl enable shairport-sync
sudo systemctl siable shairport-sync
sudo systemctl start shairport-sync
sudo systemctl stop shairport-sync
# Debug tools for shairport
sudo systemctl status shairport-sync
sudo journalctl -u shairport-sync

```
