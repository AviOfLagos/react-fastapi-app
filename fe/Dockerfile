# Use a minimal Node.js image as base
FROM node:alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the react env spinner
COPY docker-entrypoint.sh ./ 

#Populate react .env with values from env
RUN ./docker-entrypoint.sh

RUN cat .env

# Copy the rest of the application code
COPY . .

# Build the application
RUN npm run build

# Use a lightweight image for production
FROM nginx:alpine

# Copy built files from the build stage
COPY --from=build /app/build /usr/share/nginx/html
COPY --from=build /app/.env /usr/share/nginx/envs
# Expose port 80
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
 
