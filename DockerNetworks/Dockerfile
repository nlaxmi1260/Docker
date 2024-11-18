# Use the official Nginx image as the base
FROM nginx:latest

# Update the package list and install iputils-ping
RUN apt-get update && apt-get install -y iputils-ping && rm -rf /var/lib/apt/lists/*

# Copy your Nginx configuration or content if needed
# COPY ./your-nginx.conf /etc/nginx/nginx.conf

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
