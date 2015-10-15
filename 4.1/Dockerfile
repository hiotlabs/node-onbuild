FROM node:4.1

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# We install to a directory above the project so that modules will still be found
# but won't be overridden when mounting the project directory for development
# Any modules we want to override (for local testing can be mounted in via the
# host machine) and will take preference being in the project directory
ONBUILD WORKDIR /usr/src
ONBUILD COPY app/package.json /usr/src/
ONBUILD RUN npm install
ONBUILD COPY app /usr/src/app

# Reset working dir for running project commands
ONBUILD WORKDIR /usr/src/app

CMD [ "npm", "start" ]
