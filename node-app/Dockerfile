# Use the latest Node.js version with Alpine 3.21
FROM node:hydrogen-alpine3.21

# Set the working directory
WORKDIR /usr/src/app

# Install Git
RUN apk add --no-cache git

# Clone the repository
RUN git clone https://github.com/kkenan/basic-microservices.git /repo && \
    cp -r /repo/node-app/* . && \
    rm -rf /repo

# Install the app dependencies
RUN npm install


# Expose the port that your app will listen on (8081 in this case)
EXPOSE 8081

# Command to run the app
CMD ["node", "index.js"]
