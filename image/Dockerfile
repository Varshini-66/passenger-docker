# syntax=docker/dockerfile:1.4

# Define build-time arguments for architecture (ARCH) and base image name (NAME)
ARG ARCH=x86_64
ARG NAME=ubuntu

# Use the ARG variables properly with ${} for expansion in the FROM statement
FROM ${NAME}:latest

# Maintainer information
MAINTAINER Phusion <info@phusion.nl>

# Add the current directory contents to /pd_build in the container
ADD . /pd_build

# Additional build-time arguments (like proxy, if needed)
ARG http_proxy

# Use build cache to install dependencies and run the installation script
RUN --mount=type=cache,target=/build_cache \
    /usr/bin/nice /pd_build/install_image.sh

# Define the default command to run when the container starts
CMD ["/sbin/my_init"]

# Expose the necessary ports
EXPOSE 80 443
