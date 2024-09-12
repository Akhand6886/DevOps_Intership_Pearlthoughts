# Stage 1: Build the application
FROM node:20-alpine3.17 AS builder

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to install dependencies
COPY package.json ./
COPY package-lock.json ./

# Install dependencies
RUN npm install

# Copy all files to the container
COPY . .

# Build the application
RUN npm run build

# Stage 2: Create the development image
FROM node:20-alpine3.17

# Set the working directory
WORKDIR /app

# Copy the built files and node_modules from the previous stage
COPY --from=builder /app /app

# Expose the necessary port
EXPOSE 9000

# Run the application in development mode
CMD ["npm", "run", "dev"]
