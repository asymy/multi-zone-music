## Snapcast-server

- Resources
  - https://github.com/badaix/snapcast
  - https://github.com/badaix/snapcast/releases/

## Install 

- Now we can install snapcast-server which will accept input from mopidy and shairport
- Go to the releases of the snapcast git hub and copy the link for the latest release for the snap*server* for your instruction set
  - (that is armhf for raspberry pi and amd64 for x86)
```bash

cd ~ && mkdir snapcast && cd snapcast
wget https://github.com/badaix/snapcast/releases/download/v0.20.0/snapserver_x_y.deb
sudo apt install ./snapserver_x_y.deb
sudo apt-get -f install

```
## Configure
- This automatically starts snapcast-server, lets bring it down and edit the config

```bash

sudo systemctl stop snapserver
sudo nano /etc/snapserver.conf

```
- add the following lines in the stream section of the config file

```config

[stream]
stream = pipe:///tmp/snapfifo?name=default
stream = pipe:///tmp/snapfifo?name=mopidy
stream = pipe:///tmp/snapfifo-airplay?name=airplay

```

- Bring it back up and check the status (there may be an `Exception: end of file` warning - everything still works with the warning)

```bash

# Handy comands for snapserver
sudo systemctl enable snapserver
sudo systemctl disable snapserver
sudo systemctl start snapserver
sudo systemctl stop snapserver
sudo systemctl restart snapserver
# Debug tools for snapserver
sudo systemctl status snapserver
sudo journalctl -u snapserver

```