# initial layer - base image
FROM node:17-alpine


# this will tell the container to run any fuuture command inside this directory
WORKDIR /app

# the first . is where i'm copying from (host machine)
# the second . is where i'm copying to  [/app] (container) because it's relative 
COPY . .

# RUN is only used for build time and you can use as many as you want
RUN npm ci

# this is just for documentation purposes it doesn't do anything at all
EXPOSE 4000


# CMD is the command that will be run when the container is started 
CMD ["node", "app.js"]