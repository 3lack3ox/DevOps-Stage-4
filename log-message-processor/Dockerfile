# Use an official Python image as the base
FROM python:3.6-slim

# Install GCC and other build tools
RUN apt-get update && apt-get install -y \
    gcc \
    build-essential \
    python3-dev \
 && rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /app

# Copy the requirements file and install dependencies
COPY . .

RUN pip install --upgrade pip \
 && pip install -r requirements.txt

# Run the application
CMD ["python", "main.py"]

