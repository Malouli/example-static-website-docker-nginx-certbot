# Example static website with Docker, Nginx and Certbot

This is full project structure example of article [**How to dockerize your static website with Nginx, automatic renew SSL for domain by Certbot and deploy it to DigitalOcean?**](https://dev.to/koddr/how-to-dockerize-your-static-website-with-nginx-automatic-renew-ssl-for-domain-by-certbot-and-deploy-it-to-digitalocean-4cjc)

Published on [Dev.to](https://dev.to/koddr/how-to-dockerize-your-static-website-with-nginx-automatic-renew-ssl-for-domain-by-certbot-and-deploy-it-to-digitalocean-4cjc) @ 27 Jan 2020.

## Requirements

- Docker `19.x+`

## Usage

- Clone this repository and go to folder:

```console
git clone https://github.com/Malouli/website-docker-nginx-certbot.git
cd website-docker-nginx-certbot
```

- Change `site.com` to your domain at files:

```console
./docker-compose.prod.yml
./webserver/nginx/default.conf
./webserver/nginx/site.com.conf
```

- Push configured project to your own git repository.
- Connect via SSH to your droplet and `git clone` your repo.
- Check configuration of `Certbot`, start the process of obtaining SSL certificate in test mode:

```console
make certbot-test DOMAINS="crewlink-borgne.com www.crewlink-borgne.com" EMAIL=contact@crewlink-borgne.com
```

- If you see `Congratulations!`, all okay; start the process of obtaining SSL in production mode:

```console
make certbot-prod DOMAINS="crewlink-borgne.com www.crewlink-borgne.com" EMAIL=contact@crewlink-borgne.com
```

- And now, check Nginx config:

```console
make deploy-test
```

- No errors? Go your static website to production:

```console
make deploy-prod
```

- That's all!

## Updating the repo
- Go to folder and pull:

```console
cd \website-docker-nginx-certbot
git pull
```

## Author

- [Lyeos Maouli](https://github.com/Malouli)


## License

MIT
