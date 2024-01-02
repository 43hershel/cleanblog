---
title: 'Bagira: The Ultimate Guide'
description: 'A guide to the ultimate server'
date: 2022-07-08
image: '/blog-placeholder-3.jpg'
tags: ["blog", "astro"]
---
## Introduction 
This is a guide to make a home server running Linux with docker containers. Instead of being  just a step by step, I would love this to be a guide for people to **understand** what's the purpose of a home server and the components that it houses. 

**Requirements**: 
- Cheap
- Secure
- Power efficient
- Easily Backed Up
- Accessible anywhere in the world securely 

The first investment doesn't need to be insane. Work with what you have. If you have and old computer at home, even if it's slow, use it. If you don't, I bought mine for less than 100€ and slaped a 1TB Hard Drive. Still running strong to this day and I'm the happiest I've ever been with it. 

These are the services and the OS I'm running in my server. 
Running:
- Fedora Server 38
- Docker
	- Plex
	- Qbittorrent
	- Syncthing
	- homerr
- Tailscale

## The objectives
- **Why would you want a server?**: Hosting your own media, managing your backup files and photos from anywhere, learning linux and ansible, pirating...
- **How does my server work?**: Your server is hooked up to power and ethernet in your house. It runs linux and different apps inside docker containers. You can access any app from anywhere in the world and manage your files. It's a Google Drive, Netflix and 1Password combined, but much better and safer. This is just an example, you can run your apps bare metal, in Virtual Machines or however you like to. That's the beauty, you make it however nice you want.  
- **What do I need?**: Start with what you have, an old computer with a hard drive should be fine. Then scale it for your needs. Buying second hand parts is always appreciated from the enviroment. Try finding parts with low power comsuption. 

## Operating System
You could use Windows if you are really not comfortable with Linux. But Linux is far more secure in the long run, faster and it supports far more hardware than Windows does, especially older hardware. In this guide I'm using Fedora 38 Server. I would divide this 3 categories for newcomers in terms of using your server: 
- Begginner: Use Windows 10/11 with apps running bare metal
- Intermediate: Use the linux distro you like with a GUI with apps running in bare metal or docker.  
- Advance: Use Linux server edition distros with apps running inside docker containers.

## Drives
I have 2 separate drives. 
- main SSD: 256GB Kingston
- hard drive: 1TB Seagate 7200rpm

**WARNING!** Make sure you mount your drive to `/mnt` directory and change the drive permissions to read and write. If they are not, neither Plex nor qbittorrent would be able to access them. 

When it comes to hardware, I would really recommend getting a 5400rpm with an SSD for caching. In my case I used a 7200rpm drive because it is what I had in hand. But a 5400rpm drive is generally cheaper and also requires lower power consumption. Also about capacity, you should calculate the cost per GB in your country. But for a non data-hoarder, I find the sweetspot between 4 & 6 TB. That is more than enough for anyone that has a sizeable photo gallery, some flac music and quite some Anime & films stored. 

In the main SSD, aside from the system, I store files that are light and change easily: 
- Syncing my Obsidian Vault using Syncthing
- My docker containers 
- Backing up important and small files 

On the other hand, in the big hard drive I store: 
- My Plex Library 
- Music collection
- Photos  + other media 
- Time Machine Backups 


## Docker
[Docker in 100 Seconds](https://www.youtube.com/watch?v=Gjnup-PuquQ) 
- **What are they?** Virtualized enviroments that can be replicated. Each app gets it's own container. A small and light-weight virtual machine that uses the same kernel as your host system.
- **What are they for?** Recreating apps in different systems using an image (template). Same app, different enviroment, no change in the container. 
- **Why?** Docker is similar to virtualization. But instead of virtuzaling hardware components, it just virtualizes the OS. Because everything is running inside the same kernel, everything is just faster, more efficient and more secure. 
- **How does this fit into my server?**: Every app you might use is containerized inside a Docker container. So each apps has it's own dependencies and resources. Making everything independent from each other, easily replicable and easy to back-up.

### Permissions 
Before going any futher, I woud like to explain Linux permissions. This is a really important topic to tackle when you are making your server. Linux has two main users that can make changes inside the system. Root & normal user. Drives, directories and files can have different permissions. Therefore a folder that is writable by the root (privileged) user might not be writable   by the normal user. Checking permissions is a really easy way to ensure if something doesn't work. You can look up explainers through the web, but understanding permissions has been one of the most valuable things that I've done with linux inside my server.  

### Installing Docker
1. SSH into de server 
 2. Use convenience script.
``` bash
curl -fsSL https://get.docker.com -o get-docker.sh
```

 ```bash 
 sh get-docker.sh
```

When installing and initializing docker, check for status and start.

``` bash
sudo service docker start
```

``` bash
sudo service docker status
```

Then enable the service for docker to start at start up. 

 ```bash 
 sudo service docker enable
```


### Docker parts
Docker has some main components to understand. 
You have two ways of creating a docker container.
- **docker run** command: This is a command runned in your terminal that specifices all the paramenters you need. 
- **docker-compose.yml**: This is a .yaml file where you specify all the parameters and then execute in your server. (Recommended)
Inside a Docker file we have: 
- `image`: the template that the containers uses to run the app
- `container_name`: self-explanatory
- `hostname:` the name of your system
- `enviroments`: how the container is runned in terms of permissions. (Normally 1000:1000 but look `id $USER` for the id's your user has )
- `volumes`: this is where data is stored. I want to take a moment to aknowledge volumes
	- Think of volumes as where you tell the container to look. Volumes are data stored where you specified but do not worry about the path that ultimately shows inside your app. Let me explain with an example. If you run qbittorent in a docker container you first need to tell the docker file where to download files. Let's take into account that you run your container in your main SSD and the you download files to your secondary drives. Then you would specify docker this `/mnt/second_drive:download\` under the volumes file inside docker compose. When you run the container, qbittorrent is going to tell you that is downloading the files to `/downloads` which is correct but is calling the `/mnt/second_drive` the `/downloads`. Is the same place named differently. So just specify your volumes and thats it. 
- `ports`: exposed ports in the containers that can communicate outside. 

### Managing containers 
As many containers you might have, managing them is really important too. You could use a tool like [Portrainer](https://www.portainer.io/) for container managment but I like to have everything runned from the terminal myself. Therefore I use [Lazydocker](https://github.com/jesseduffield/lazydocker). It's just a way of managing containers from the terminal. To install it: 

1. Download the binaries from github in the releases page. I recommend you check out the github page to download the most up to date version.

```bash
wget   https://github.com/jesseduffield/lazydocker/releases/download/v0.21.1/lazydocker_0.21.1_Linux_arm64.tar.gz 

# Careful with the ARM64 or x86 versions 
```

2. Use the tar command to decompress the file

``` bash
tar zxf lazydocker_0.20.0_Linux_x86_64.tar.gz
```

3. Install it in the /usr/local/bin 

``` bash
sudo install lazydocker /usr/local/bin
```

Running the command `lazydocker` should be enough to start the service. 


### Docker Compose & Containers
These are the different docker-compose files & docker run commands I used. I would be explaining them 1 by 1. These are commented, don't copy them. It's for sake of understanding and them doing them by yourself. 

Plex: ([docker info](https://docs.linuxserver.io/images/docker-plex))

```yml
---
version: "2.1"
services:
plex:
image: lscr.io/linuxserver/plex:latest
container_name: plex # <-- name of the container
ports:  # <-- specifies ports
- "8200:32400/tcp" 
- "8201:32400/udp"
environment:
- PUID=1000 # <-- how the container runs, permissions as user, NOT AS ROOT
- PGID=1000
- TZ=Europe/Madrid # <-- timezone
- VERSION=docker
- PLEX_CLAIM= #https://www.plex.tv/claim/ <-- this token is used for claiming the server. Just write whatever the website generate in here.
volumes:
- /mnt/docker:/config # <-- where you mount you volume for config
- /mnt:/media # <-- where you mount you volume for config
restart: unless-stopped
```

syncthing: ([docker info](https://github.com/syncthing/syncthing/blob/main/README-Docker.md))

```yaml
---
version: "3"
services:
  syncthing:
    image: syncthing/syncthing
    container_name: syncthing
    hostname: "your server name"
    environment:
      - PUID=1000
      - PGID=1000
    volumes:
      - "your path where is stored":/var/syncthing
    ports:
      - 8384:8384 # Web UI
      - 22000:22000/tcp # TCP file transfers
      - 22000:22000/udp # QUIC file transfers
      - 21027:21027/udp # Receive local discovery broadcasts
    restart: unless-stopped
```

qbittorrent: ([docker info](https://docs.linuxserver.io/images/docker-qbittorrent))

```yaml
---
version: "2.1"
services:
  qbittorrent:
    image: lscr.io/linuxserver/qbittorrent:latest
    container_name: qbittorrent
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Madrid
      - WEBUI_PORT=8080
    volumes:
      - "/path/to/config":/config
      - "/path/to/downloads":/downloads
    ports:
      - 8080:8080
      - 6881:6881
      - 6881:6881/udp
    restart: unless-stopped
```

watchtower: 

``` yaml
version: "3" 
services: 
	watchtower: 
	image: containrrr/watchtower 
	volumes: - /var/run/docker.sock:/var/run/docker.sock

```


## Connection
For connecting to your server, the are three main ways. 
- SSH: Connecting remotely to the terminal on your server. 
- Tailscale VPN: Connecting remotely to any service + ssh to your server through a Zero-Trust VPN 
- SFTP: Connecting remotely to your server file trees. 

### SSH Hardening 
Your main configuration of the server will be though SSH. We are going to create a hardened version of SSH with what is called a private/public key pair. This is a pair of files that you generate with your computer that enable you and just you, the owner of that key pair, to access the server. This also enables password-less login to your server, which makes it really convinient for accessing ssh & it's also more secure. 

To create a SSH key pairs and making the usable:  [Harden SSH](https://www.youtube.com/watch?v=l1iu3iZq1aQ) + [article](https://tonyteaches.tech/ssh-security/)
1. Generate an SSH key pair on each computer: Use the `ssh-keygen` command on each computer to generate an SSH key pair (public and private key).	
2. Copy the public key to the server: On each computer, copy the contents of the public key (located in the `~/.ssh/id_rsa.pub` file) to the server's `authorized_keys` file. You can do this by using the `ssh-copy-id` command or manually appending the public key to the `authorized_keys` file on the server. 
3. Test the SSH connection: Once the public key is added to the server's `authorized_keys` file, you should be able to SSH into the server from any of the computers without entering a password. Use the `ssh` command followed by the username and hostname ip of the server to test the connection.
4. Edit the `sshd_config` file and disable `PasswordAuthentication`,  `PermitEmptyPasswords no` & `UsePAM no`. Also `PermitRootLogin no`. 
5. Change default port from 22 to another. SSH normally uses port 22 in your router to connect to the server. Change the port to another one that is not as vunerable to attacks.

### Tailscale 
Tunnel your connection with [Tailscale · Best VPN Service for Secure Networks](https://tailscale.com/)
https://tailscale.com/
Normally, for you to be able to connect to your server, you use a Dynamic DNS and the connect to it using that IP. You could use something like NO-IP service. This solves a really simple but annoying problem. Your ISP (Internet Service Provider) changes your public IP every "X" amount of time for protection. If your public IP did not change, attackers or pretty much anyone with knowledge could attack your home network. But it also opposes inconvinience from connecting to your server remotedly. 

Tailscale is just a Zero-Trust VPN that directly connects you to your server. It is, by far, the most comfortable and secure way that I've tried to connect to my server. No public IP, no port-forward literally just sign up, in your server and clients, connect to it though the admin panel and DONE. 

#### **MAGIC DNS**
This is probably the best feature of Tailscale. When you are going to ssh to your server or adding a seaching a webui related to your server, Magic DNS replaces your server VPN IP with the name you gave your server. If your server has XXX.XX.XX.XX has the IP, it replaces it with your_server_name.  This does not only work for DNS in the web clients, but also for ssh for example. Making this process 100x more simple. 

- SSH Before MagicDNS: ssh user@110.11.10.20 
- SSH After MagicDNS: ssh user@servername 

Tailscale also gives you uptime of your devices in general. In the admin console, you can find which devices are connected to your tailscale network. This work if you keep your devices permanently connected. 

## Provisioning, maintanence and automation 

- Docker
The Docker WatchTower containers 

- Back ups (Cron)
Backing up docker containers

- Ansible
Ansible is a automation tool written in Python. Learning it, could be a useful tool to automate updates and installation of your server. It functions by modules, playbooks and config files. 

### Possible issues: 
Plex container: 
port 32400 not openned 
- If you are unable to access the web UI, there could be a few reasons for this:
 1.  Firewall: Make sure that the firewall on your Fedora Server is not blocking incoming traffic on port 32400. You can check this by running the following command in the terminal:

    sudo firewall-cmd --list-all
    
If port 32400 is not listed as allowed, you can open it using the following command:

    sudo firewall-cmd --add-port=32400/tcp --permanent sudo firewall-cmd --reload

### Extra Recursos
https://github.com/TechSquidTV/UltimateHomeServer 

## Upgrading the server to new versions of Fedora

To upgrade the server to newer versions of Fedora without making an installation media from scratch, just use the following commands:

```shell
sudo dnf system-upgrade download --releasever=VERSION
```

```shell
sudo dnf system-upgrade reboot
```

```shell
sudo dnf system-upgrade clean
```
