# base image
FROM node:lts-alpine3.13

# set working directory
WORKDIR /usr/nodejs_app/src

# copy source files to working directory
COPY . .

# init project and install dependencies
RUN npm init --yes && \
    npm install express --save

# expose application's port
EXPOSE 3000

# run application
CMD [ "node", "app.js" ]