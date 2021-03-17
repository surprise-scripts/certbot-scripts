# certbot-wildcard
Script for generating wildcard certificate

```bash
certbot-auto certonly \
  --manual \
  --preferred-challenges=dns \
  --email your@email.com \
  --server https://acme-v02.api.letsencrypt.org/directory \
  --agree-tos \
  -d example.com, *.example.com
```
