FROM ubuntu:16.04

# Update apt
RUN apt-get update && apt-get upgrade -y

# Install basic utilities
RUN apt-get install build-essential git wget sudo grep software-properties-common apt-transport-https ca-certificates gnupg tar curl zip nano vim unzip --no-install-recommends -y
RUN apt-get install python3 python3-pip python3-wheel --no-install-recommends -y

# Add Ubuntu test ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test

# Add llvm key
RUN wget --progress=dot:giga -O - https://apt.llvm.org/llvm-snapshot.gpg.key | gpg --dearmour -o /usr/share/keyrings/llvm.gpg

# Add llvm apt repositories
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial main" >>"/etc/apt/sources.list.d/llvm.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-12 main" >>"/etc/apt/sources.list.d/llvm-12.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-11 main" >>"/etc/apt/sources.list.d/llvm-11.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-10 main" >>"/etc/apt/sources.list.d/llvm-10.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-9 main" >>"/etc/apt/sources.list.d/llvm-9.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-8 main" >>"/etc/apt/sources.list.d/llvm-8.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-7 main" >>"/etc/apt/sources.list.d/llvm-7.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-6.0 main" >>"/etc/apt/sources.list.d/llvm-6.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-5.0 main" >>"/etc/apt/sources.list.d/llvm-5.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-4.0 main" >>"/etc/apt/sources.list.d/llvm-4.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-3.9 main" >>"/etc/apt/sources.list.d/llvm-3.9.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/xenial/ llvm-toolchain-xenial-3.8 main" >>"/etc/apt/sources.list.d/llvm-3.8.list"

# Update apt with new llvm packages
RUN apt-get update

# Install C++ packages
RUN apt-get install gcc gcc-9 gcc-8 gcc-7 gcc-6 gcc-5 gcc-4.9 gcc-4.8 gcc-4.7 --no-install-recommends -y
RUN apt-get install gcc-multilib gcc-9-multilib gcc-8-multilib gcc-7-multilib gcc-6-multilib gcc-5-multilib gcc-4.9-multilib gcc-4.8-multilib gcc-4.7-multilib --no-install-recommends -y
RUN apt-get install g++ g++-9 g++-8 g++-7 g++-6 g++-5 g++-4.9 g++-4.8 g++-4.7 --no-install-recommends -y
RUN apt-get install g++-multilib g++-9-multilib g++-8-multilib g++-7-multilib g++-6-multilib g++-5-multilib g++-4.9-multilib g++-4.8-multilib g++-4.7-multilib --no-install-recommends -y
RUN apt-get install clang clang-* --no-install-recommends -y
RUN apt-get install lld lld-* --no-install-recommends -y
RUN apt-get install clang-tidy clang-tidy-12 --no-install-recommends -y
RUN apt-get install clang-format clang-format-12 --no-install-recommends -y
RUN apt-get install libc++1 --no-install-recommends -y
RUN apt-get install libc++abi1 --no-install-recommends -y
RUN apt-get install cmake cmake-curses-gui cppcheck iwyu ccache gdb ninja-build --no-install-recommends -y

# Install vcpkg
RUN git clone https://github.com/microsoft/vcpkg /opt/vcpkg

# Bootstrap vcpkg
RUN /opt/vcpkg/bootstrap-vcpkg.sh -disableMetrics
RUN /opt/vcpkg/vcpkg integrate bash

# Update apt
RUN apt-get update && apt-get upgrade -y

# Cleanup
RUN apt-get autoremove -y && apt-get clean
