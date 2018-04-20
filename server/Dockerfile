FROM node:alpine

LABEL MAINTAINER="Amit Prabhu"

# Create app directory
WORKDIR /usr/src/app

# Bundle APP files
COPY package*.json ./
COPY pm2.json .

# Install app dependencies
RUN npm install

# Install pm2 so we can run our application
RUN npm i -g pm2

COPY src src/

RUN ls -la
EXPOSE 3000
CMD [ "pm2", "start", "pm2.json", "--no-daemon" ]