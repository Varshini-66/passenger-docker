# syntax=docker/dockerfile:1.4

# Define build-time arguments for ARCH and NAME
ARG ARCH=x86_64
ARG NAME=ubuntu

# Use the ARG variables properly with `${}` for expansion
FROM ${NAME}-base:latest-${ARCH}

# Maintainer information
MAINTAINER Phusion <info@phusion.nl>

# Add the current directory to the image's /pd_build folder
ADD . /pd_build

# Define additional build-time arguments (proxy, if needed)
ARG http_proxy

# Install dependencies and run the installation script using a build cache for improved performance
RUN --mount=type=cache,target=/build_cache \
    /usr/bin/nice /pd_build/install_image.sh

# Define the default command to run when the container starts
CMD ["/sbin/my_init"]

# Expose necessary ports
EXPOSE 80 443
