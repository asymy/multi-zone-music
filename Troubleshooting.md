# Troubleshooting

## Mopidy cant write to the pipe
- I had some problems with permission with the pipe outputs
  - Stop all the services
  - Run the following:

```bash

sudo sysctl fs.protected_fifos=0

```

- If this fixes the issue then you have to rerun the command on startup
- TODO: find better way
- source: 
  - https://unix.stackexchange.com/questions/503111/group-permissions-for-root-not-working-in-tmp

## Volume output on raspberry pi is low

- On the raspberry pi use the command `alsamixer` to increase the volume to the maximum
- Make sure the raspberry pi is set to the right output