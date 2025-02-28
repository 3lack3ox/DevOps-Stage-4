# Stage 1: Build Vue.js App
FROM node:14-alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application
RUN npm run build

# Stage 2: Serve with a lightweight server
FROM node:14-alpine

# Set working directory
WORKDIR /app

RUN npm install -g serve

# Copy the built application from the builder stage
COPY --from=build /app/dist .

# Expose the necessary port
EXPOSE 8080

# Run the application
CMD ["serve", "-s", ".", "-l", "8080"]
