# base image
FROM node
# label
LABEL MAINTAINER=MAIKS
# inside the container what would be the default working directory
# pwd 
# wrkdir /usr/src/app
WORKDIR /usr/src/app
# copy dependencies - app folder
COPY package*.json ./
# copy all files with .json to working directory
# run npm commands
RUN npm install  -g npm@7.20.6

# COPY EVERYTHING FROM CURRENT LOCATION & PASTE IN DEFAULT LOCATION
COPY . .
# expose the port
EXPOSE 3000

# cmd ["node","app.js"]
CMD ["node", "app.js"]