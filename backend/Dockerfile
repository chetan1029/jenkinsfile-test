#### Stage 1: Build the node application
FROM node:12.18.0-alpine as build

RUN apk add --no-cache bash
RUN apk add --no-cache curl



# Configure the main working directory inside the docker image.
# This is the base directory used in any further RUN, COPY, and ENTRYPOINT 
# commands.
WORKDIR /app

# Copy the package.json as well as the package-lock.json and install 
# the dependencies. This is a separate step so the dependencies 
# will be cached unless changes to one of those two files 
# are made.
COPY package.json ./
#COPY ../parser-api ./parser-api

RUN npm install --production
#RUN npm upgrade
# If you are building your code for production
# RUN npm ci --only=production

# Copy the main application
COPY . ./

# Expose port 3000 to the Docker host, so we can access it 
# from the outside.
EXPOSE 8889 8890

CMD [ "node", "app.js" ]
