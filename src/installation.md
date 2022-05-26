# Installation

This guide is for installing Zerologin on your own server. If you want to use a running instance (like [zerologin.co](https://zerologin.co)), please check [How to use Zerologin on my website](/how-to-use-zerologin)

## Prerequisite
- Node.js LTS >= 16.5.0
- Yarn
- PostgreSQL >= 13 (< 13 not tested)

> For a better Node.js version management, you can use [Volta](https://volta.sh/)

## Clone & install
``` bash
git clone https://github.com/zerologin/zerologin.git
cd zerologin
yarn install
```

## Setup variables environment
Duplicate `.env.example` file to `.env` and change these variables
```
APP_URL=http://localhost:3333 # it should be localhost:3333 in dev and your domain name in production
APP_KEY=
PG_HOST=localhost
PG_PORT=5432
PG_USER=root
PG_PASSWORD=root
PG_DB_NAME=zerologin
JWT_SECRET=ChangeMe
```

`APP_KEY` can be generated using the command `node ace generate:key`. This param will be used to encrypt users jwt secrets

## DB migrations
```bash
node ace migration:run
```

## Launch
``` bash
yarn dev
```
Your application is now running under the port `3333`

[http://localhost:3333](http://localhost:3333)

## Production preparation

`.env` file can be used in production but you can also use your environment variables from your OS or your provider dashboard UI.

After you cloned or pulled the repository and your env are configured, follow these steps
```bash
yarn build #.env will be copied if exists and DB migrations will be done at this step
cd build/
yarn install --production
node server.js # or use ecosystem.config.js with pm2
```

### Reverse proxy using Caddy

[Caddy](https://caddyserver.com/) can easily be used as reverse proxy. Here is an example Caddyfile.

The tls on_demand is required for automatic TLS certificats delivering for your users. 

```
http://myzerologin-instance.com {
  reverse_proxy localhost:3333
}

:443 {
  reverse_proxy localhost:3333

  tls your@email.com {
    on_demand
  }
}
```