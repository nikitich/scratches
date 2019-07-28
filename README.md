# Docker Installation

* #### Uninstall old versions:
```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```
* #### Update the `apt` package index:
```
$ sudo apt-get update
```
* #### Install packages to allow `apt` to use a repository over HTTPS:
```
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
* #### Add Docker’s official GPG key:
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
* #### Add current stable repository for yours release:
```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
* #### Update the `apt` package index:
```
$ sudo apt-get update
```
* #### Install the latest version of Docker CE and containerd:
```
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```
* #### Check the result:
```
$ sudo docker run hello-world
```
* #### Create the docker group:
```
$ sudo groupadd docker
```
* #### Add your user to the docker group:
```
$ sudo usermod -aG docker $USER
```
* #### Reboot:
```
$ sudo reboot
```
* #### Verify that you can run docker commands without sudo:
```
$ docker run hello-world
```
### Install docker-compose
> The preferred way to install `docker-compose` is thru the `python-pip`
* #### Update the `apt` package index:
```
$ sudo apt-get update
```
* #### Install the pip
```bash
$ sudo apt-get install python-pip
```
* #### Install `docker-compose`
```bash
$ sudo pip install docker-compose
```


```bash
$ sudo apt-get install python-pip
$ sudo pip install docker-compose
```

* #### Setup docker

Check docker-compose configuration:
```bash
docker-compose config
```

On very first start of this configuration or on cofirutaion update, you should up the configuration with the `--build` key 
```bash
docker-compose up -d --build
```
On regular start:
```bash
docker-compose up -d
```

If you need to watch the output of echo server in dev mode:
```bash
docker-compose up | grep node_
```

For checking current status:
```bash
docker-compose ps
```

If everything is ok you should see something like this:
```bash
     Name                    Command               State                                Ports                              
---------------------------------------------------------------------------------------------------------------------------
project_db_1      docker-entrypoint.sh mysqld      Up      0.0.0.0:3366->3306/tcp                                          
project_main_1    /entrypoint supervisord          Up      0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp, 0.0.0.0:9001->9000/tcp
project_node_1    laravel-echo-server start  ...   Up      0.0.0.0:6001->6001/tcp                                          project_redis_1   docker-entrypoint.sh redis ...   Up      0.0.0.0:6379->6379/tcp 
```


* #### Install Dependencies

```bash
docker-compose exec main composer install --working-dir=/var/www/project/src/backend
```

```bash
docker-compose exec --workdir=/var/www/project/src/backend main npm install
```
