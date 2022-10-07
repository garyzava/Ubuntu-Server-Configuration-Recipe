# Ubuntu Server Configuration Recipe

**NOTE**: This guide does not cover the actual installation of Ubuntu. Use at your own risk. Basic configuration is applied here - DYOR.

Basic configuration commands to have your Ubuntu Server up and running on production.

<br />

<hr />

## Overview

* [Update And Upgrade](#update-and-upgrade)
* [Enable Firewall](#enable-firewall)
* [Install Further Tools](#install-further-tools)
* [Install Further Applications](#install-further-applications)

<br />

<hr />

## Update And Upgrade

* `sudo reboot` Restart and wait for some time and the Linux server will reboot itself
* `sudo apt-get update`
* `sudo apt-get upgrade`

And sometimes:

* `sudo apt-get dist-upgrade`

### New Distribution?

If there is a new release upgrade:

* `do-release-upgrade`

<br />

<hr />

## Enable Firewall

UFW (Uncomplicated Firewall) is installed by default on Ubuntu. If it has been uninstalled for some reason, you can install it with `sudo apt install ufw`.

* `sudo vi /etc/default/ufw`. Check `IPV6=yes`
* `sudo ufw reset`
* `sudo ufw status verbose`. Should show inactive
* `sudo ufw default deny incoming`
* `sudo ufw default allow outgoing`
* `sudo ufw allow ssh` or `sudo ufw allow 22`. Allowing Secure Shell (SSH)
* `sudo ufw enable`
* `sudo ufw status verbose`. Should show active

### Allowing Other Connections

* `sudo ufw allow http` or `sudo ufw allow 80`. **HTTP** on port 80, which is what unencrypted web servers use.
* `sudo ufw allow https` or `sudo ufw allow 443`. **HTTPS** on port 443, which is what encrypted web servers use

Reference: https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04

<br />

<hr />

## Install Further Tools

* `sudo timedatectl set-timezone UTC`. Set Timezone UTC/GMT+0
* `sudo apt-get install net-tools` to install tools for commands like `ifconfig -a` (network interface) and `netstat`
* `sudo apt install openssh-server`. You should already have this installed so this command won't do anything

<br />

<hr />

## Install Further Applications

### Angular (and Node.js)

* `curl -fsSL https://deb.nodesource.com/setup_17.x | sudo -E bash -`. Download Node.js
* `sudo apt-get install -y nodejs`. Install Node.js
* `sudo npm install -g @angular/cli`. Install Angular CLI

Reference: https://github.com/nodesource/distributions/blob/master/README.md

### PostgreSQL
