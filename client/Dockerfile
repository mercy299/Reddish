# Use an official Node.js base image with version 14
FROM node:20.4-alpine3.17 as development

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Run npm build; this outputs build files to a dist or build folder
RUN npm run build

FROM nginx as production-stage

RUN mkdir /app

COPY --from=development /app/build /app

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx.conf /etc/nginx/conf.d/nginx.conf


# Expose port 80
EXPOSE 80

# Specify the command to run the application
CMD [ "nginx", "-g", "daemon off;" ]

