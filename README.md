# Dokku

Please refer to [https://github.com/progrium/dokku](https://github.com/progrium/dokku).

## What has been modified

Docker installation related has been all removed, which means it can be installed on server with **pre-installed docker** and **Linode** that doesn't compatible with aufs.

## Requirements

- A fresh VM running Ubuntu `14.04 x64`

## Installing

To install docker on Ubuntu, please run the following commands:

    wget -qO- https://get.docker.com/ | sh

To install this special version of dokku, you can run the following bootstrapper command:

	wget https://raw.githubusercontent.com/Evlos/dokku/0.3.21.1/bootstrap.sh
    sudo DOKKU_BRANCH=0.3.21.1 bash bootstrap.sh

The reason of using this special version is the commits so far contains many fixes, I will write warnings if there is problem happened on my production environment.

After the installation, set the ssh key for user: dokku on your server.

	cat ~/.ssh/id_rsa.pub | ssh your-server-address "sudo sshcommand acl-add dokku progrium"

And add git remote address to the app your want to deploy.

	git remote add server dokku@your-server-address:node-js-app
	git push server master
