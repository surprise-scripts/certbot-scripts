# certbot-scripts

A collection of one-ish liners for generating certificates with certbot because I have a terrible memory and the internets documentation sucks

## Wildcard (dns verification)

```bash
certbot-auto certonly \
  --manual \
  --preferred-challenges=dns \
  --email your@email.com \
  --server https://acme-v02.api.letsencrypt.org/directory \
  --agree-tos \
  -d example.com, *.example.com
```

You will have to update your own DNS with this. This is acceptable in my use cases because wildcards are carefully tracked.

You may receive a message saying "NET::ERR_CERTIFICATE_TRANSPARENCY_REQUIRED". This is normal (in chrome) for the first 30 minutes. see: https://community.letsencrypt.org/t/certificate-transparency-logging-delay/94071/2 check: https://crt.sh/

# Multi-SAN (with web verification)

```bash
certbot certonly --webroot -w /var/www/html -d www.example.com -d example.com
```

This will use /var/www/html to handle certificate generation. It's worth mentioning that I do have httpd configured to work very well with this. 

If you want to do multiple second level domains, with different webroots, this is from the certbot docs:

```bash
certbot certonly --webroot -w /var/www/html -d www.example.com -d example.com -w /var/www/example2 -d www.example2.com -d example2.com
```
