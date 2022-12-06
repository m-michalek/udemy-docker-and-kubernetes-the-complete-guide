# Dockerfile

####### STEP ONE #######

# tags the stage with the name builder
# tagging it mean that from this line all following steps are part of the builder phase / step
FROM node:16-alpine as builder

WORKDIR "/app"

COPY package.json .
RUN npm install

COPY . .

CMD ["npm", "run", "build"]

####### STEP ONE #######


####### STEP TWO #######

# every FROM statement indicate a seperate stage / step
FROM nginx

# copy from the builder containert the build directory into the new container
# the directory to place the build files is predefined by nginx
COPY --from=builder /app/build /usr/share/nginx/html

# we dont need a explicit command to start nginx
# the nginx developers already configured a startup command in the nginx Docker image

####### STEP TWO #######