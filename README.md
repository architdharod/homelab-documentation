# homelab-documentation

## Networking: 

Goals: 

- homelab services are only accessible via tailnet.
- services use domain name *.hl.dharod.de
- use a suitable reverse proxy to access (preferably traefik)
- network has to be secured/encrypted end to end

## homelab1 server

1. Dashy

2. Tailscale


## homelab2 server

1. Caddy

Caddyfile: 
```
(cloudflare) {
  tls {
    dns cloudflare {env.CLOUDFLARE_API_TOKEN}
  }
}

# homelab dashboard "dashy"
homelab.int.dharod.de {
  reverse_proxy http://192.168.1.2:8080
  import cloudflare
}
```
