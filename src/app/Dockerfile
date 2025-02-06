# Use the official Node.js 16 Alpine image as the base image
FROM node:16-alpine3.13

# Define build-time arguments
ARG IMAGE_CREATE_DATE
ARG IMAGE_VERSION
ARG IMAGE_SOURCE_REVISION

# Set metadata labels
LABEL org.opencontainers.image.title="Hello Kubernetes!" \
      org.opencontainers.image.description="Provides a demo app to deploy to a Kubernetes cluster. It displays a message, the name of the pod and details of the node it is deployed to." \
      org.opencontainers.image.created=$IMAGE_CREATE_DATE \
      org.opencontainers.image.version=$IMAGE_VERSION \
      org.opencontainers.image.authors="Paul Bouwer" \
      org.opencontainers.image.url="https://hub.docker.com/r/paulbouwer/hello-kubernetes/" \
      org.opencontainers.image.documentation="https://github.com/paulbouwer/hello-kubernetes/README.md" \
      org.opencontainers.image.vendor="Paul Bouwer" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.source="https://github.com/paulbouwer/hello-kubernetes.git" \
      org.opencontainers.image.revision=$IMAGE_SOURCE_REVISION

# Create the app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# Copy package.json and install dependencies
COPY package.json /usr/src/app/
RUN npm install

# Copy the rest of the application code
COPY . /usr/src/app

# Switch to a non-root user for security
USER node

# Define the command to run the app
CMD [ "npm", "start" ]
