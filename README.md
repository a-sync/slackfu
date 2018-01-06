# slackfu

## Requirements
 * bash compatible shell
 * sane install of curl

## Installation
 1. download and unpack the [archive](https://github.com/a-sync/slackfu/archive/master.tar.gz)
 2. enter the unpacked directory and make [slackfu](slackfu) executable
 3. set [your authentication token](https://api.slack.com/custom-integrations/legacy-tokens/) in the SLACK_AUTH_TOKEN variable of [slackfu](slackfu#L3)
 4. create a global symbolic link
```bash
curl -sL https://github.com/a-sync/slackfu/archive/master.tar.gz | tar xz
cd slackfu-master && chmod +x slackfu
read -p "Enter authentication token: " SLACKAT && sed -i "3s|.*|SLACK_AUTH_TOKEN=\"$SLACKAT\"|" slackfu
sudo ln -s "$(readlink -f slackfu)" /usr/local/bin
```

## Usage
```
Usage: slackfu [options] <file>

Options:
    -r <channel name|channel ID>
    -n <file name>
    -t <title text>
    -f <initial comment>
    -T <authentication token>

Examples:
    slackfu somefile.jpg
    slackfu -r general -n "filename.log" < somefile.txt
    ps | slackfu -r C8P15L0TV -t "$(id -un) $(hostname -f)"
    ls -la /etc/ | slackfu -r D024BE91L,random -f "$(history 1)"
```
