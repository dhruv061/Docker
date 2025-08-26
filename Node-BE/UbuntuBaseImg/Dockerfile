FROM ubuntu:22.04

WORKDIR /usr/src/app

#Set node version
ARG NODE_VERSION=20.x

# Install only necessary packages and clean up after
RUN apt-get update && \
    apt-get install -y --no-install-recommends curl ca-certificates && \
    curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION} | bash - && \
    apt-get install -y --no-install-recommends nodejs && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Copy only package files first to CACAHE npm install
COPY package*.json ./

#--omit=dev Means Don't install devDependencies — only install dependencies
RUN npm install --omit=dev

# Now copy the rest of the app
COPY . .

EXPOSE 4011

CMD ["node", "index.js"]