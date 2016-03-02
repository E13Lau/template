# Vapor Example

Fork this example project as a boilerplate for working with Vapor.

Check out the [live demo](http://vapor.qutheory.io) running on Ubuntu.

## Badges

[![Build Status](https://travis-ci.org/qutheory/vapor-example.svg?branch=master&style=flat-square)](https://travis-ci.org/qutheory/vapor-example)
[![PRs Welcome](https://img.shields.io/badge/prs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![Slack Status](http://slack.tanner.xyz:8085/badge.svg?style=flat-square)](http://slack.tanner.xyz:8085)

## Documentation

View [Vapor](https://github.com/qutheory/vapor) for documentation.

## Requirements

Swift 2.2 or later is required.

Works on Ubuntu, Docker, Heroku, OS X

## Building

Clone this repo and run `./run` to start your application.

You can also build it manually by running `swift build` to download the
dependencies, then run `.build/debug/App`. 

Note: the `run` script may contain fixes for bugs in SPM that may prevent you
from building with `swift build`.

If you are having issues running, try clearing your downloaded files with
`./clear`. Also, checkout Kylef's
[swiftenv](https://github.com/kylef/swiftenv) for ensuring you have the latest
version of Swift installed. If you have `swiftenv`, run `swiftenv install` inside your root folder to
install the proper version of Swift.

## Deploying

Check the [Vapor](https://github.com/qutheory/vapor) documentation for more in-depth deployment instructions.

To deploy to Ubuntu 14.04 LTS (without Swift installed on remote server).

1. Compile program on Ubuntu 14.04 (Swift must be installed on this computer)
2. Copy program from `.build/[debug,release]/App` into `Deploy/App`
3. Copy contents of `Deploy` folder to remote Ubuntu 14.04 server (the folder contains all shared libs needed for running)
4. Run `./run.sh`

### Upstart

To start your `Vapor` site automatically when the server is booted, add this file to your server.

`/etc/init/vapor-example.conf`

```conf
description "Vapor Example"

start on startup

exec /home/<user_name>/vapor-example/.build/release/App --workDir=/home/<user_name>/vapor-example
```

You additionally have access to the following commands for starting and stopping your server.

```shell
sudo stop vapor-example
sudo start vapor-example
```

The following script is useful for upgrading your website.

```shell
git pull
swift build --configuration release
sudo stop vapor-example
sudo start vapor-example
```

### Heroku / Swifton.me

[![Deploy to Swifton.me](https://serve.swifton.me/badge.png)](https://serve.swifton.me/oneclick?repository=https://github.com/tannernelson/vapor-example)

### Docker
You can run this demo application locally in a Linux environment using Docker.

1. Ensure [Docker](https://www.docker.com) is installed on your local machine.
2. Start the Docker terminal
3. cd into `vapor-example`
4. Build the container `docker build -t vapor .`
5. Run the container `docker run -it -p 8080:8080 vapor`
5. Configure VirtualBox to [forward ports 8080 to 8080](https://www.virtualbox.org/manual/ch06.html)
6. Visit http://0.0.0.0:8080
