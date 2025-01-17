#### Stage 1: Build the react application
FROM node:14-alpine as build

RUN apk add --no-cache bash
RUN apk add --no-cache curl

# openssl req -nodes -new -x509 -keyout server.key -out server.cert

# Configure the main working directory inside the docker image. 
# This is the base directory used in any further RUN, COPY, and ENTRYPOINT 
# commands.
WORKDIR /app

# Copy the package.json as well as the package-lock.json and install 
# the dependencies. This is a separate step so the dependencies 
# will be cached unless changes to one of those two files 
# are made.
COPY package.json  ./
RUN npm config set @eds:registry https://arm.rnd.ki.sw.ericsson.se/artifactory/api/npm/proj-eds-npm-local
RUN npm i @eds/vanilla@3.12.0 --force
RUN apk add git
RUN npm install

# If you are building your code for production
# RUN npm ci --only=production

# Copy the main application
COPY . ./

# Expose port 3000 to the Docker host, so we can access it
# from the outside.
EXPOSE 3000


CMD [ "npm", "start" ]
