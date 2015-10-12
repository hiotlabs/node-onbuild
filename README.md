# node-onbuild

Like official docker node onbuild image, with a few changes:

1. assuming the node app source is located in local subfolder `app`.
2. installing npm packages one level up in `/usr/src`, making way for having the local `app` folder mounted as a volume.
 
## building

```bash
$ docker build -t hiotlabs/node-onbuild:4.1 .
```

## credits
Ideas come from 
http://www.grahamgilchrist.com/blog/2015/05/13/node-packages-docker-and-node-onbuild-container 
and https://github.com/b00giZm/docker-compose-nodejs-examples