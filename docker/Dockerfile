FROM ubuntu:20.04

# Update the package lists
RUN apt-get update

# Set non-interactive mode
ENV DEBIAN_FRONTEND=noninteractive

# Install any necessary packages
RUN apt-get install -y \
    git \
    curl \
    gcc \
    g++ \ 
    cmake \
    zlib1g-dev

# Set the working directory
WORKDIR /opt

# Clone the repository
RUN git clone --recursive https://github.com/lbcb-sci/racon.git racon
WORKDIR /opt/racon
RUN mkdir build
WORKDIR /opt/racon/build
RUN cmake -DCMAKE_BUILD_TYPE=Release ..
RUN make
RUN make install

# test the installation
RUN racon --version

# Set the run command
CMD ["racon"]

# docker build -f docker/Dockerfile -t racon-test .