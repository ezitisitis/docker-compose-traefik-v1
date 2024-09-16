# Traefik v1 docker-compose

This repository contains docker-compose with traefik v1.
This docker-compose should be used only for local development, but You can
update it for production usage (at one's own risk).

## Documentation:

* [Traefik](https://docs.traefik.io/v1.7/)
* [Docker](https://docs.docker.com/compose/)

## Installation

Copy and edit `traefik.toml`:
```bash
cp traefik.toml.example traefik.toml
vi traefik.toml
```

Run docker-compose:
```bash
docker-compose up -d
```

## Usage

### Dashboard

Traefik dashboard is available by: [http://127.0.0.1:8080](http://127.0.0.1:8080)

### Networking

Add Your container to traefik network, by adding next lines in Your 
docker-compose:
```yml
networks:
  frontend:
    external:
      name: traefik_gateway
```

and also add this to container network:
```yml
    labels:
      - traefik.backend=backend_name
      - traefik.frontend.rule=Host:host_of_your_application.localhost
      - traefik.port=80
      - traefik.docker.network=traefik_gateway
    networks:
      - backend
      - frontend
```

## Credits

- [Marks Bogdanovs](https://www.ezitisitis.com)
