# Installation

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
PG_HOST=localhost
PG_PORT=5432
PG_USER=root
PG_PASSWORD=root
PG_DB_NAME=zerologin
JWT_SECRET=ChangeMe
```

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