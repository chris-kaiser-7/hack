# Use the official Debian base image
FROM debian:latest

# Set environment variable to avoid interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Update package index and install curl
RUN apt-get update && \
    apt-get install -y docker && \
    rm -rf /var/lib/apt/lists/*

# Set default command
CMD ["bash"]
