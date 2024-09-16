# Use the official Nginx image as a base
FROM nginx:latest

# If you don't have a custom configuration file, you can omit this line
# COPY nginx.conf /etc/nginx/nginx.conf

# Copy static content to the Nginx directory in the container
COPY index.html /usr/share/nginx/html/index.html

# Expose port 80 to access the web server
EXPOSE 80

# Command to run Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
