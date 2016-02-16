# node-onbuild

Like official docker node onbuild image, but we're installing
npm packages one level above the app folder. Modules will still
be found but won't be overridden when mounting the project
directory for development.

# Breaking change
2016-02-16: Now using `CMD [ "node", "app.js" ] instead of `npm start`, due to
npm not forwarding signals such as SIGTERM.

## Use in development setup
Dockerfile:

```
FROM hiotlabs/node-onbuild:latest
RUN npm install -g supervisor
```

docker-compose.yml:

```
node:
  build: .
  volumes:
    - .:/usr/src/app
  command: supervisor -e js,json app.js
```

## Credits
Ideas come from [here](http://www.grahamgilchrist.com/blog/2015/05/13/node-packages-docker-and-node-onbuild-container) and [there](https://github.com/b00giZm/docker-compose-nodejs-examples).
