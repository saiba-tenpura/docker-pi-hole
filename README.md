# Docker Pi-hole
My personal Docker Pi-hole setup using an external Traefik instance for serving the web interface and Unbound instance as independent upstream DNS.

## Environment Variables
The `.env` file allows you to configure the basic attributes of the Pi-hole service.

| Variable          | Default               | Value              | Description                                        |
| ----------------- | --------------------- | ------------------ | -------------------------------------------------- |
| `PIHOLE_URL`      | `pi-hole.example.com` | `<URL>`            | URL under which the Pi-hole instance is reachable. |
| `PIHOLE_PASSWORD` | unset                 | `<Admin password>` | Admin password for logging into the web interface. |
| `PIHOLE_TZ`       | `America/Chicago`     | `<Timezone>`       | Timezone used for performing log rotations.        |
