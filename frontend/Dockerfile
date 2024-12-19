# Use the official Node.js image
FROM node:22 AS build

# Set working directory
WORKDIR /app

COPY package*.json ./
RUN npm install

# Copy all files and build the project
COPY . ./
RUN npm run build

# Serve the build output using a static file server
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
