# Use Ubuntu 18.04 as the base image
FROM ubuntu:18.04

# Install necessary packages and dependencies
RUN apt update && apt install -y \
    build-essential \
    gcc \
    git \
    libsdl2-dev \
    mesa-utils \
    libgl1-mesa-glx \
    x11-apps \
    wget \
    apt-transport-https \
    ca-certificates \
    gnupg

# Install CMake manually (version 3.20 as an example)
RUN wget https://github.com/Kitware/CMake/releases/download/v3.20.0/cmake-3.20.0-linux-x86_64.sh && \
    chmod +x cmake-3.20.0-linux-x86_64.sh && \
    ./cmake-3.20.0-linux-x86_64.sh --skip-license --prefix=/usr/local && \
    rm cmake-3.20.0-linux-x86_64.sh

# Set the working directory in the container
WORKDIR /app

# Copy the entire project into the container
COPY . .

# Create a build directory, configure, and build the project using CMake
RUN rm -rf build && mkdir -p build && cd build && cmake .. && make -j3

# Set the default command to run the executable (adjust path to match actual build output)
CMD ["./bin/main"]
