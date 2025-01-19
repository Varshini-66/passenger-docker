# syntax=docker/dockerfile:1.4

# Define build-time arguments for architecture (ARCH) and base image name (NAME)
ARG ARCH=x86_64
ARG NAME=ubuntu

# Use the ARG variables properly with ${} for expansion in the FROM statement
FROM ${NAME}:latest

# Maintainer information
MAINTAINER Phusion <info@phusion.nl>

# Add the contents from the 'image' folder to /pd_build in the container
ADD image/ /pd_build/

# Define additional build-time arguments (like proxy, if needed)
ARG http_proxy

# List the contents of /pd_build to verify the script is copied
RUN ls -l /pd_build/

# Run the installation script, ensuring it's copied to /pd_build
RUN --mount=type=cache,target=/build_cache /usr/bin/nice /pd_build/install_image.sh

# Define the default command to run when the container starts
CMD ["/sbin/my_init"]

# Expose the necessary ports
EXPOSE 80 443
