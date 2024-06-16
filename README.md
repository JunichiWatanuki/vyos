# VyOS(1.5-rolling)

## Check vyos on docker to make sure it works.
The VyOS Docker image used here is the one created according to the procedure described on the official VyOS website.
It will be the one uploaded on DockerHub at [https://hub.docker.com/r/jwat/vyos](https://hub.docker.com/r/jwat/vyos).

The procedure for creating a Docker image conforms to `VyOS 1.5 (circinus,current)`, which is available at [https://docs.vyos.io/en/latest/contributing/build-vyos.html](https://docs.vyos.io/en/latest/contributing/build-vyos.html).

### Clone this repository.

```
git clone git@github.com:JunichiWatanuki/vyos.git
```

### Go to the cloned directory.

```
cd vyos
```

### Creating the configuration file for the VyOS container by copying the sample file as is.

```
cp .env.sample .env
```

### Create a container.

```
docker compose -f docker-compose.yml build --no-cache
```

### Start the container.

```
docker compose -f docker-compose.yml up -d
```

### Run the command to confirm that the vyos user has been created in the VyOS container.

```
docker exec -it test-vyos-VyOS ls -la /home/
```

### Execute the above command, and if it is displayed as shown in the bottom line below, move on to the next step.
(If the vyos user cannot be confirmed, wait a few minutes and run the command again to confirm that the vyos user has been created in the VyOS container.)

```
$ docker exec -it test-vyos-VyOS ls -la /home/
total 12
drwxr-xr-x 1 root root  4096 Jun 15 04:33 .
drwxr-xr-x 1 root root  4096 Jun 15 04:30 ..
drwxr-xr-x 3 vyos users 4096 Jun 15 04:38 vyos
```

### Access the VyOS container as a vyos user.

```
docker exec -it test-vyos-VyOS su - vyos
```

### If you want to customize the initial configuration, edit `sample.config` in advance

```
vi vyos/opt/vyatta/etc/config/config.boot
```
