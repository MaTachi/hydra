# Hydra

Personal website and blog.

Author: Daniel Jonsson  
License: [MIT License](LICENSE)

## Run with Docker

Build the Docker image:

    $ sudo docker build -t matachi/hydra .

Run the image:

    $ sudo docker run -i -t -v `pwd`:`pwd`:rw -p 127.0.0.1:8000:8000 -p 127.0.0.1:1337:22 matachi/hydra

In the container, `cd` into the project folder, which is located at the same
path as on the host. Then start the Django development web server with:

    $ python3 manage.py runserver 0.0.0.0:8000

## Configure PyCharm

To work with the project in PyCharm and still run it in Docker, read the
following text.

Set your project Python interpreter to a remote interpreter. Configure it with
the following settings:

    Host: 127.0.0.1
    Port: 1337
    Username: root
    Auth type: Password
    Password: pass
    Python interpreter path: /usr/bin/python3
    PyCharm helpers path: /root/.pycharm_helpers

And before starting a *Django server*, configure the host IP to `0.0.0.0:8000`.

## Build JS and CSS

### Prerequisites

Install Node.js, npm, gulp and virtualenv.

#### Debian and Ubuntu

Instructions to install the prerequisites on a Debian based system (Ubuntu for
example):

    $ sudo apt-get install nodejs python-virtualenv
    $ sudo npm install -g gulp
    $ sudo chown -R `whoami`:`whoami` ~/.npm ~/tmp

#### Fedora

Instructions for Fedora:

    $ sudo dnf install nodejs npm python-virtualenv
    $ sudo npm install -g gulp

Note, use `yum` instead of `dnf` if `dnf` isn't available.

### Setup

Install build tools and dependencies:

    $ npm install

Note, the above command will also execute [postinstall.sh](postinstall.sh).

### Build

    $ gulp build

## Manually build the syntax highlighting stylesheet

This is already done by `$ gulp build`.

    $ pygmentize -S manni -f html -a ".codehilite pre" > manni.css

## Manually build Social Share Privacy

This is already done by `$ gulp build`.

Download from <https://github.com/panzi/SocialSharePrivacy> and run:

    $ ./build.sh -m tumblr,twitter,facebook -l none
