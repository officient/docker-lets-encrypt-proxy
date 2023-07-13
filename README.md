> ⚠️ This repository has been migrated to [Azure Devops](https://dev.azure.com/ExactGroup/Officient)

# docker-lets-encrypt-proxy

Nginx Reverse Proxy automatically managing Let's Encrypt certificates

Environment variables:

* `ORIGIN_HOST` main server hostname or ip address (eg https://www.domain.com ) 

# Instructions for deploying to AWS

* Create a new Amazon ECS cluster
* Make sure ports 80 and 443 are open to all inbound traffic
* Create a new ECS task pointing to this repo, make sure the ORIGIN_HOST variable is set
* Deploy the task to the ECS cluster
* Point new domains to the ECS cluster

## Building locally

In case you need to look around in the container image locally, you can build and run it.

```bash
docker build --platform linux/x86_64 .

docker images
# replace `30c` with part of your newly built image
docker run --rm -it --platform=linux/amd64 -e ORIGIN_HOST=https://google.com 30c

docker ps
# replace `4f32` with part of your newly running container
docker exec -it 4f32 /bin/sh

# now you have a shell where you can check-out `openssl` or other installed binaries
```
