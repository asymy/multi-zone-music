# Installing Mopidy

 - Resources:
   - https://mopidy.com
   - https://github.com/mopidy/mopidy
   - https://docs.mopidy.com/en/latest/installation/

```bash

wget -q -O - https://apt.mopidy.com/mopidy.gpg | sudo apt-key add -
sudo wget -q -O /etc/apt/sources.list.d/mopidy.list https://apt.mopidy.com/buster.list
sudo apt update
sudo apt install mopidy -y

```
## Install Add ons
- Resources
  - https://mopidy.com/ext/spotify/
  - https://github.com/mopidy/mopidy-spotify
  - https://mopidy.com/ext/local/
  - https://github.com/mopidy/mopidy-local
  - https://mopidy.com/ext/youtube/
  - https://github.com/natumbri/mopidy-youtube

```bash

apt search mopidy
sudo apt install -y mopidy-mpd mopidy-spotify mopidy-local
sudo python3 -m pip install Mopidy-YouTube

```

## Install Iris
- Resources
  - https://github.com/jaedb/Iris
  - https://mopidy.com/ext/iris/

```bash

sudo python3 -m pip install Mopidy-Iris

```

# Configuring Mopidy

- Resources
  - https://docs.mopidy.com/en/latest/running/service/
  - https://docs.mopidy.com/en/latest/config/
  - https://github.com/badaix/snapcast/blob/master/doc/player_setup.md#mopidy
  - 
- If running as a service (which we will do so it can run in background and also auto run on start up), the configuration file lives at `/etc/mopidy/mopidy.conf`. You can also check the current configuration by running `sudo mopidyctl config`.
- Remeber to check the configuration parameters of any extra add ons you want to use.
- In general, don't put values in your configuration which is already at the default. This will be handled by mopidy
```bash

sudo mopidyctl config
sudo nano /etc/mopidy/mopidy.conf

```

```config
[mpd]
hostname = ::

[http]
Hostname = ::
default_app = iris

[audio]
output = audioresample ! audioconvert ! audio/x-raw,rate=48000,channels=2,format=S16LE ! filesink location=/tmp/snapfifo-mopidy

[iris]
country = GB
locale = en_GB

[spotify]
username = ********
password = ********
client_id = ********
client_secret = ********
bitrate = 320

```

- Check your config is working by starting and checking the status of mopidy
- We can enable mopidy at this point to so it starts automatically on boot

```bash

sudo systemctl enable mopidy
sudo systemctl start mopidy
sudo systemctl status mopidy

```
- Go to the web interface to check that iris is working at http://ip.of.music.server:6680
- Then bring down mopidy again
```bash

sudo systemctl stop mopidy

```
```bash

# Handy comands for mopidy
sudo systemctl enable mopidy
sudo systemctl disable mopidy
sudo systemctl start mopidy
sudo systemctl stop mopidy
sudo systemctl restart mopidy
# Debug tools for mopidy
sudo systemctl status mopidy
sudo journalctl -u mopidy

```
