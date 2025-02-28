# Stage 1: Build the Go application
FROM golang:1.21-alpine AS builder

WORKDIR /app

# Copy Go modules and download dependencies
COPY go.mod go.sum ./
RUN go mod download

# Copy the rest of the application files
COPY . .

# Build the application
RUN go build -o auth-api

# Stage 2: Create a smaller runtime container using golang:1.21-alpine
FROM golang:1.21-alpine

WORKDIR /app

# Copy the built binary from the builder stage
COPY --from=builder /app/auth-api .

# Expose the necessary port (change if needed)
EXPOSE 8081

# Run the application
CMD ["./auth-api"]
