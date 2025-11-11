# FROM node:20.19.4

# # Set the working directory
# WORKDIR /app

# # Copy package.json and package-lock.json
# COPY package*.json ./

# RUN npm install
# RUN npm install -g nodemon

# # Copy the rest of the application code
# COPY . .

# # Expose the port the app runs on
# EXPOSE 1234

# # Start the application
# CMD ["npm", "run", "dev"]



FROM node:18-slim

# Install required build tools and dependencies
RUN apt-get update && \
    apt-get install -y python3 make g++ && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copy package files
COPY package*.json ./

# Clean install dependencies and rebuild bcrypt
RUN npm ci && \
    npm rebuild bcrypt --build-from-source

# Copy application code
COPY . .

EXPOSE 1234

CMD ["npm", "run", "dev"]