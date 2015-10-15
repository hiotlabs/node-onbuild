# node-onbuild

Like official docker node onbuild image, with a few changes and additions:

1. assuming the node app source is located in local subfolder `app`.
2. installing npm packages one level up in `/usr/src`, making way for having the local `app` folder mounted as a volume in dev.
3. include nodemon for smoother dev cycles.

## use

Assuming a folder structure such as:

```
.
├── docker-compose.yml
└── node
    ├── app
    │   ├── app.js
    │   └── package.json”
    └── Dockerfile
```


`node/Dockerfile`:

```
FROM hiotlabs/node-onbuild:4.1
```


Then we can have a `docker-compose.yml` for development:

```
node:
  build: ./node
  volumes:
    - ./node/app:/usr/src/app
  ports:
    - "3000:3000"
  command: nodemon -L app.js
```

## credits
Ideas come from [here](http://www.grahamgilchrist.com/blog/2015/05/13/node-packages-docker-and-node-onbuild-container) and [there](https://github.com/b00giZm/docker-compose-nodejs-examples).
