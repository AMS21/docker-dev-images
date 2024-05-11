FROM ubuntu:22.04

# Update apt
RUN apt-get update && apt-get upgrade -y

# Install basic utilities
RUN apt-get install build-essential git wget sudo grep software-properties-common gpg gnupg gpg-agent tar curl zip unzip nano vim fzf --no-install-recommends -y
RUN apt-get install python3 python-is-python3 python3-pip python3-wheel --no-install-recommends -y

# Add Ubuntu test ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test -y -n

# Add llvm key
RUN wget --progress=dot:giga -O - https://apt.llvm.org/llvm-snapshot.gpg.key | gpg --dearmour -o /usr/share/keyrings/llvm.gpg

# Add llvm apt repositories
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy main" >>"/etc/apt/sources.list.d/llvm.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-18 main" >>"/etc/apt/sources.list.d/llvm-18.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-17 main" >>"/etc/apt/sources.list.d/llvm-17.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-16 main" >>"/etc/apt/sources.list.d/llvm-16.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-15 main" >>"/etc/apt/sources.list.d/llvm-15.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-14 main" >>"/etc/apt/sources.list.d/llvm-14.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/jammy/ llvm-toolchain-jammy-13 main" >>"/etc/apt/sources.list.d/llvm-13.list"

# Update apt with new llvm packages
RUN apt-get update

# Install C++ packages
RUN apt-get install gcc gcc-14 gcc-13 gcc-12 gcc-11 gcc-10 gcc-9 --no-install-recommends -y
RUN apt-get install gcc-multilib gcc-14-multilib gcc-13-multilib gcc-12-multilib gcc-11-multilib gcc-10-multilib gcc-9-multilib --no-install-recommends -y
RUN apt-get install g++ g++-14 g++-13 g++-12 g++-11 g++-10 g++-9 --no-install-recommends -y
RUN apt-get install g++-multilib g++-14-multilib g++-13-multilib g++-12-multilib g++-11-multilib g++-10-multilib g++-9-multilib --no-install-recommends -y
RUN apt-get install clang clang-* --no-install-recommends -y
RUN apt-get install lld lld-* --no-install-recommends -y
RUN apt-get install libclang-rt-19-dev libclang-rt-18-dev libclang-rt-17-dev libclang-rt-16-dev libclang-rt-14-dev --no-install-recommends -y
RUN apt-get install llvm-runtime llvm-*-runtime --no-install-recommends -y
RUN apt-get install clang-tidy clang-tidy-18 --no-install-recommends -y
RUN apt-get install clang-format clang-format-18 --no-install-recommends -y
RUN apt-get install clang-tools clang-tools-18 --no-install-recommends -y
RUN apt-get install libc++1 --no-install-recommends -y
RUN apt-get install libc++abi1 --no-install-recommends -y
RUN apt-get install cmake cmake-curses-gui cppcheck iwyu ccache gdb ninja-build --no-install-recommends -y

# Install python packages
RUN pip3 --no-cache-dir install gcovr cmakelang pyyaml

# Install vcpkg
RUN git clone https://github.com/microsoft/vcpkg /opt/vcpkg

# Bootstrap vcpkg
RUN /opt/vcpkg/bootstrap-vcpkg.sh -disableMetrics
RUN /opt/vcpkg/vcpkg integrate bash

# Update apt
RUN apt-get update && apt-get upgrade -y

# Cleanup
RUN apt-get autoremove -y && apt-get clean
