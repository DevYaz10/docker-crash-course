# initial layer - base image
FROM node:17-alpine

# install nodemon globally (-g) so we can use it anywhere in the container
# in the package.json you should add "dev": "nodemon -L app.js" to activate nodemon 
RUN npm install -g nodemon

# this will tell the container to run any fuuture command inside this directory
WORKDIR /app

# Copy package-related files first to leverage Docker's caching mechanism
COPY package.json package-lock.json* ./

# RUN is only used for build time and you can use as many as you want
# npm ci does a clean install based on the exact versions in package-lock.json
RUN npm ci

# the first . is where i'm copying from (host machine)
# the second . is where i'm copying to  [/app] (container) because it's relative 
COPY . .

# this is just for documentation purposes it doesn't do anything at all
EXPOSE 4000


# CMD is the command that will be run when the container is started 
CMD ["npm", "run", "dev"]



# to build the image
# docker build -t [image_name:tag] .


# to run the container
# docker run --name [container_name] -p [host_port]:[container_port] --rm -v [host_path]:[container_working_dir] -v [container_working_dir]/node_modules [image_name:tag]
#? the --rm flag removes the container when it is stopped
#? the first -v flag is for volume mounting ( to sync files changes between host and container)
#? the second -v flag is for volume mounting ( to prevent node_modules from being overwritten by the host's node_modules)
#? the [host_path] is the path to the directory on the host machine
#? the [container_working_dir] is the path to the directory on the container


# to stop the container
# docker stop [container_name]