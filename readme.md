# equation-cloud-https-proxy

This repository combines [nginx-proxy](https://github.com/jwilder/nginx-proxy), [docker-gen](https://github.com/jwilder/docker-gen) and [docker-letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion) to provide an HTTPS proxy for the [Equation Cloud web app](https://github.com/equation-cloud/equation-cloud-front-end). It is based on [Karl Fathi's examples](https://github.com/pixelfordinner/pixelcloud-docker-apps/tree/master/nginx-proxy).

## Setup
Create an external docker network named 'nginx-proxy':

```
docker network create -d bridge nginx-proxy
```

You'll only need to do this once.

## Running
Start the HTTPS proxy containers using the Docker Compose file from this repository:

```
git clone https://github.com/equation-cloud/equation-cloud-https-proxy

cd equation-cloud-https-proxy

docker-compose up — build -d
```

Start the web application container.

The container to be proxied must define certain environment variables and be connected to the 'nginx-proxy' docker network. See the Docker Compose file in the web application repository for details.

## Debugging

You should use the Docker Compose 'logs' command to see the output of the daemonized containers.
