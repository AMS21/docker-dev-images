FROM alpine:latest

RUN apk update

RUN apk add --no-cache \
    bash \
    build-base \
    ccache \
    clang15 \
    clang16 \
    clang17 \
    clang18 \
    clang18-extra-tools \
    cmake \
    curl \
    gcc \
    gdb \
    git \
    gnupg \
    g++ \
    grep \
    include-what-you-use \
    libc-dev \
    lld \
    lldb \
    llvm-runtimes \
    llvm15 \
    llvm16 \
    llvm17 \
    llvm18 \
    make \
    nano \
    ninja \
    python3 \
    python3-dev \
    sudo \
    tar \
    unzip \
    vim \
    wget \
    zip

# Install vcpkg
RUN git clone https://github.com/microsoft/vcpkg /opt/vcpkg

# Bootstrap vcpkg
RUN touch /root/.bashrc
RUN /opt/vcpkg/bootstrap-vcpkg.sh -disableMetrics
RUN /opt/vcpkg/vcpkg integrate bash
