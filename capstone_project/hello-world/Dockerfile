# Uses a oficial node image and a 
FROM node:16.13.1 

# Set the path for do all the work
WORKDIR /tmp/node_app

# Copy the project files to te work directory
# The first dot indicate the current directory were is located the Dockerfile
# The second dot indicate the basepath of the work directory
COPY . .

# Install all dependencies
RUN npm install

# Set the de default command to iniciate the container
CMD [ "npm", "start"]