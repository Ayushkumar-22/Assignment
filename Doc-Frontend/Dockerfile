# Use an appropriate Node.js base image
FROM node:16 as build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json for installing dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Build the React application
RUN npm run build

# Use a lightweight server to serve the built files
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 for the frontend service
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
