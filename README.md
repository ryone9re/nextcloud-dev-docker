# Enviroment for developing nextcloud application

## How to use

Put in your app to the `nextcloud/apps/` directory.

Then run it

```Shell
docker-compose up -d --build
```

After execution, nextcloud developing container will launch at `localhost:8080`.

Proceed to setup.

_notice: you should not install recommended apps if you want to test your app only._

## Build with

- Ubuntu
  - 20.04 focal
- PHP
  - 7.4
- Node.js
  - 16.13.1
- Nextcloud
  - 22.2.3
