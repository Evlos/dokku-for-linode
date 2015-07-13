# Dokku

Please refer to [https://github.com/progrium/dokku](https://github.com/progrium/dokku).

## What has been modified in this forked version

Docker installation related has been all removed, which means it can be installed on server with **pre-installed docker** and **Linode** that doesn't compatible with aufs.

## Installing

To install docker on Ubuntu, please run the following commands:

    sudo apt-get update
    sudo apt-get install docker.io
    sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker

To install the latest **unstable** version of dokku, you can run the following bootstrapper command:

    $ wget -qO- https://raw.githubusercontent.com/Evlos/dokku/0.2.3.1/bootstrap.sh | sudo bash

The reason of using **unstable** version is the commits so far contains many fixes, I will write warnings if there is problem happened on my production environment.

After the installation, set the ssh key for user: dokku on your server.

	$ cat ~/.ssh/id_rsa.pub | ssh your-server-address "sudo sshcommand acl-add dokku progrium"

And add git remote address to the app your want to deploy.

	$ git remote add public dokku@your-server-address:node-js-app
	$ git push public master
