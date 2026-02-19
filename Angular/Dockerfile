# Use lightweight Nginx image
FROM nginx:alpine
 
# Copy Angular build output to Nginx HTML directory
COPY dist/cricket-project/index.html /usr/share/nginx/html
 
# Expose HTTP port
EXPOSE 80
 
