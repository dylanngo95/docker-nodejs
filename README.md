# Docker NodeJS

Docker support run NodeJS and NextJS support

* node: 16.4.2
* nginx: 1.16.1

# How to use

## Init Project

```bash
git clone https://github.com/dylanops/docker-nodejs.git

cd docker-nodejs

mv .env.sample .env.sample

mv conf/nginx/nextjs.conf.sample conf/nginx/default.conf

# Change server name
vim conf/nginx/default.conf

# Change nextjs path
// .env
PROJECT_PATH=/home/dylan/nextjs

```

## Create self credentials
```bash
cd /conf/nginx
openssl req -newkey rsa:4096 \
            -x509 \
            -sha256 \
            -days 3650 \
            -nodes \
            -out local.crt \
            -keyout local.key
```

## Start service

```bash
docker-compose up -d

# Start nextjs
docker exec -ti node bash
ls -al
yarn
yarn start
```