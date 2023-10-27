FROM httpd:2.4

# Update and install vim
RUN apt-get update && apt-get install -y vim

# Use the default command from the httpd:2.4 image to start the server
CMD ["httpd-foreground"]