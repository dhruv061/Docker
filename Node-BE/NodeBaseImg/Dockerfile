FROM node:20-alpine

WORKDIR /usr/src/app

# Copy package files and install only production dependencies
COPY package*.json ./

#--omit=dev Means Don't install devDependencies — only install dependencies
RUN npm install --omit=dev

# Copy the rest of the application code
COPY . .

EXPOSE 4011

CMD ["node", "index.js"]
