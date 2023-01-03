FROM ubuntu:22.04

# Update apt
RUN apt-get update && apt-get upgrade -y

# Install basic utilities
RUN apt-get install build-essential git wget sudo grep software-properties-common gpg tar curl zip unzip fzf \
    python3 python-is-python3 python3-pip python3-wheel \
    --no-install-recommends -y

# Add Ubuntu test ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test -y -n

# Add llvm key
RUN wget --progress=dot:giga -O - https://apt.llvm.org/llvm-snapshot.gpg.key | gpg --dearmour -o /usr/share/keyrings/llvm.gpg

# Add llvm apt repositories
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy main" >> "/etc/apt/sources.list.d/llvm.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-15 main" >> "/etc/apt/sources.list.d/llvm-15.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-14 main" >> "/etc/apt/sources.list.d/llvm-14.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-13 main" >> "/etc/apt/sources.list.d/llvm-13.list"

# Update apt with new llvm packages
RUN apt-get update

# Install C++ packages
RUN apt-get install ninja-build \
    gcc gcc-12 gcc-11 gcc-10 gcc-9 \
    gcc-multilib gcc-12-multilib gcc-11-multilib gcc-10-multilib gcc-9-multilib \
    g++ g++-12 g++-11 g++-10 g++-9 \
    g++-multilib g++-12-multilib g++-11-multilib g++-10-multilib g++-9-multilib \
    clang clang-15 clang-14 clang-13 clang-12 clang-11 \
    lld lld-15 lld-14 lld-13 lld-12 lld-11 \
    clang-tidy clang-tidy-15 \
    clang-format clang-format-15 \
    clang-tools clang-tools-15 \
    libc++1 \
    libc++abi1 \
    cmake cppcheck iwyu ccache gdb \
    --no-install-recommends -y

# Install python packages
RUN pip3 --no-cache-dir install gcovr cmakelang pyyaml

# Install vcpkg
RUN git clone https://github.com/microsoft/vcpkg /opt/vcpkg

# Bootstrap vcpkg
RUN /opt/vcpkg/bootstrap-vcpkg.sh -disableMetrics
RUN /opt/vcpkg/vcpkg integrate bash

# Cleanup
RUN apt-get autoremove -y && apt-get clean