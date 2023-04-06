# Uses a oficial node image and specify a version of node to use
FROM node:16.13.1 as build

# Set the path for do all the work
WORKDIR /tmp/node_app

# Copy the project files to te work directory
# The first dot indicate the current directory were is located the Dockerfile
# The second dot indicate the basepath of the work directory
COPY . .

# Install all dependencies
RUN npm install
# Create a buil 
RUN npm run build

# Set the de default command to iniciate the container
# CMD [ "npm", "start"]

# Configure the build in a Apache Server
FROM httpd:2.4

# Copy the build to the path of apache server
COPY --from=build /tmp/node_app/build /usr/local/apache2/htdocs/