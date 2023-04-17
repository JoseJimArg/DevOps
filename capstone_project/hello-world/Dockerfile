# Uses a oficial node image and specify a version of node to use
FROM node:16.13.1 as build


# Commands for setup ssh and create user for it
RUN apt-get update  -y \
    && apt-get upgrade -y \ 
    && apt-get install -y \
    ssh \
    sshpass \
    sudo \
    software-properties-common


RUN useradd -rm -d /home/node_user -s /bin/bash -g root -G sudo -u 1001 node_user
RUN echo node_user:clavecita123 | chpasswd
RUN echo "node_user ALL=(ALL:ALL) NOPASSWD: ALL" |  EDITOR="tee -a"  visudo

# Set the path for do all the work
WORKDIR /home/node_user

# Copy the project files to te work directory
# The first dot indicate the current directory were is located the Dockerfile
# The second dot indicate the basepath of the work directory
COPY . .

# Copy the file to start the ssh service
COPY startup.sh .

# Install all dependencies
RUN npm install

EXPOSE 3000

# Create a buil 
# RUN npm run build

# Set the de default command to iniciate the container
# CMD ["npm", "start"]

CMD /bin/bash /home/node_user/startup.sh & npm start

# Configure the build in a Apache Server
# FROM httpd:2.4
# 
# WORKDIR /usr/local/apache2/
# 
# Copy the build to the path of apache server
# COPY --from=build /tmp/node_app/build /usr/local/apache2/htdocs/
# 