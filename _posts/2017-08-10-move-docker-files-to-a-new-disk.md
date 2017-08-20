---
layout: post
title: Move docker files to a new disk
---

As more and more containers start running in your docker swarm, you may encounter the following exception.

```
failed to register layer: Error processing tar file(exit status 1): open *** : no space left on device.
```

As the error message says itself, the disk on your server is full. By default, docker engine stores its downloaded images and running containers in ```/var/lib/docker```, so you can see exactly how much space it has taken with the following command.

```
# du -h --max-depth=0 /var/lib/docker
9.8G    /var/lib/docker
```

It's very easy to purchase an additional data disk and mount to this location if your server is hosted in the cloud, such as AWS EC2 or Aliyun ECS instances.

Firstly, let's format the new disk.

```
sudo mkfs.ext4 /dev/vdb1
```

Then, backup data in ```/var/lib/docker```, mount this disk here and move the data back.

```
sudo service docker stop
sudo mv /var/lib/docker /var/lib/docker_data

sudo mkdir /var/lib/docker
sudo mount -t ext4 /dev/vdb1 /var/lib/docker

sudo mv /var/lib/docker_data/* /var/lib/docker/

sudo service docker start
df
```

In my experience, moving data from the backup folder to the new disk took a long time, so it'd better be done in the first place when you are installing the docker engine.