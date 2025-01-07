# Shared Services / Infrastructure

This Repository contains compose files for various stacks which provide shared services across the Docker Swarm.

## Running

First, create the shared web network for other stacks to use for Traefik.

```sh
docker network create -d overlay web
```

Then, deploy the shared services stack

```sh
docker stack deploy -c ./traefik-stack.yaml traefik
docker stack deploy -c ./swarmpit-stack.yaml swarmpit
```

## Traefik Routing

To enable routing from Traefik to the applications, you'll need the following labels:

```yaml
labels:
  - "traefik.enable=true"
  - "traefik.http.routers.<app-name>.rule=Host(`<domain-name>`)"
  - "traefik.http.routers.<app-name>.entrypoints=websecure"
  - "traefik.http.services.<app-name>.loadbalancer.server.port=<http-port>"
  - "traefik.http.routers.<app-name>.tls.certresolver=myresolver"
  - "traefik.docker.network=web"
```
