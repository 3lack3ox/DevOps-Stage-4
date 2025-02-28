# Stage 1: Build Stage
# Use the Node.js image for building the application
FROM node:carbon-alpine AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy the package.json and package-lock.json to the container
COPY package*.json ./

# Install the dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Stage 2: Runtime Stage
# Use a smaller Node.js runtime image
FROM node:carbon-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy only the necessary files from the builder stage
COPY --from=builder /app /app

# Expose the port the service will run on
EXPOSE 8082

# Run the application
CMD ["npm", "start"]

