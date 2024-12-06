# Docker Pi-hole
This repository contains my Docker Compose configuration for setting up a Pi-hole instance with Unbound as its underlying recursive DNS resolver and an external Traefik instance for serving the web interface.

## Features
* Runs a Pi-hole instance which is reachable via IPv4 and IPv6 over the hosts DNS port.
* Uses Unbound as the default DNS resolver, providing an independent recursive DNS service.
* Adds container labels for exposing the Pi-hole interface via an external Traefik instance via the `proxy-network`.
* IPv6 connectivity for Docker containers via a IPv6 Unique Local Address (ULA).

## Usage
First clone the repository, then copy and adjust the enviroment configuration file to your liking.
```bash
cp .env.example .env
```

After that setup the external Traefik instance and network a short guide can be found [here](https://github.com/saiba-tenpura/traefik-proxy).

In order to support IPv6 via Docker you have to adjust your configuration accordingly.
```
# /etc/docker/daemon.json
{
    "experimental": true,
    "ip6tables": true,
    "userland-proxy": true
}
```

Once launched, your instance can serve as a DNS server. Initially, however, you may experience slower performance due to the time it takes for it to propagate downwards from the root DNS servers and build up its cache.
```
docker compose up -d
```

## Environment Variables
The `.env` file allows you to configure the basic attributes of the Pi-hole service.

| Variable          | Default               | Value              | Description                                        |
| ----------------- | --------------------- | ------------------ | -------------------------------------------------- |
| `PIHOLE_URL`      | `pi-hole.example.com` | `<URL>`            | URL under which the Pi-hole instance is reachable. |
| `PIHOLE_PASSWORD` | unset                 | `<Admin password>` | Admin password for logging into the web interface. |
| `PIHOLE_TZ`       | `America/Chicago`     | `<Timezone>`       | Timezone used for performing log rotations.        |

## License
This project is licensed under the MIT License.
