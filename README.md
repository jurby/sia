# sia

- [https://mtlynch.io/sia-via-docker/](https://mtlynch.io/sia-via-docker/)

## build

```
# Create a Docker image tagged with the label "sia"
$ sudo docker build --tag sia .
# OR run jurby/sia container

```

## run

```
# NOTE: Replace 10.0.0.101 with the IP address of your Synology NAS on your
# local network.
# Ubuntu - get local Ip address: hostname -I | cut -d' ' -f1
$ LOCAL_IP=`hostname -I | cut -d' ' -f1`

```

```
# Create a Docker container based on the Sia image and start running it in the
# background.
$ sudo docker run \
  --detach \
  --publish "${LOCAL_IP}:9980:8000" \
  --publish 9981:9981 \
  --publish 9982:9982 \
  --volume /nas/sia:/mnt/sia \
  --name sia-container jurby/sia
```

OR
```
# Create a Docker container based on the Sia image and start running it in the
# background.
$ sudo docker run \
  --detach \
  --publish "`hostname -I | cut -d' ' -f1`:9980:8000" \
  --publish 9981:9981 \
  --publish 9982:9982 \
  --volume /nas/sia:/mnt/sia \
  --name sia-container jurby/sia
```
