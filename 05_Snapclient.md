# Snapcast-client

- Resources
  - https://github.com/badaix/snapcast
  - https://github.com/badaix/snapcast/releases/

## Install 

- This will be installed on the endpoint raspberry pis (may also be installed elsewhere) ...
- Go to the releases page of snapcast github and copy the link for the latest release for the snap*client* for your instruction set
  - (that is armhf for raspberry pi and amd64 for x86)

```bash

cd ~ && mkdir snapcast && cd snapcast
wget https://github.com/badaix/snapcast/releases/download/v0.20.0/snapclient_x_y.deb
sudo apt install ./snapclient_x_y.deb
sudo apt-get -f install

```
## Configure

- This will start snapclient by default
- Use the comand `snapclient -h` to see if you need to change any parameters 
- You can add these argument to the file at `/etc/default/snapclient`
- The client should be auto-detected by the server

```bash

# Handy comands for snapclient
sudo systemctl enable snapserver
sudo systemctl disable snapclient
sudo systemctl start snapserver
sudo systemctl stop snapserver
sudo systemctl restart snapclient
# Debug tools for snapclient
sudo systemctl status snapclient
sudo journalctl -u snapclient

```
