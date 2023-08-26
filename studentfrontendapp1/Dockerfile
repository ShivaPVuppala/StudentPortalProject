# Use a Node.js-specific base image
FROM node:14

# Install unzip and update the package list
RUN apt-get update && apt-get install -y unzip

# Set the working directory
WORKDIR /app

# Copy the ZIP file to the working directory
COPY com/ui/test/smfrontui.zip /app/smfrontui.zip

# Unzip the ZIP file
RUN unzip smfrontui.zip

# Move into the unzipped directory
WORKDIR /app/studentfrontendapp1

# Copy package.json and package-lock.json to the working directory
COPY package*.json /app/studentfrontendapp1/

# Install dependencies
RUN npm install

# Build the application
RUN npm run build

# Expose the specified port
EXPOSE $PORT

# Set environment variables
ENV NUXT_HOST=0.0.0.0
ENV NUXT_PORT=$PORT
ENV PROXY_API=$PROXY_API
ENV PROXY_LOGIN=$PROXY_LOGIN

# Run the application
CMD [ "npm", "start" ]
