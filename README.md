# node-onbuild

Like official docker node onbuild image, but we're installing
npm packages one level above the app folder. Modules will still
be found but won't be overridden when mounting the project
directory for development.

## development setup

`Dockerfile`:

```
FROM hiotlabs/node-onbuild:4.1
RUN npm install -g supervisor
```

`docker-compose.yml`:

```
node:
  build: .
  volumes:
    - .:/usr/src/app
  command: supervisor -e js,json app.js
```
## credits
Ideas come from [here](http://www.grahamgilchrist.com/blog/2015/05/13/node-packages-docker-and-node-onbuild-container) and [there](https://github.com/b00giZm/docker-compose-nodejs-examples).
