# Stage 1: Build React app with Node.js 23
FROM node:23-alpine AS builder

WORKDIR /usr/src/app

# Copy package.json and lock files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all files and build React app
COPY . .
RUN npm run build


# Stage 2: Serve with Nginx
FROM nginx:alpine

# Copy custom Nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy React build files from builder stage
COPY --from=builder /usr/src/app/dist /usr/share/nginx/html

# Expose port
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]