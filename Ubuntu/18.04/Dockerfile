FROM ubuntu:18.04

# Update apt
RUN apt-get update && apt-get upgrade -y

# Install basic utilities
RUN apt-get install build-essential git wget sudo grep software-properties-common gpg gnupg gpg-agent tar curl zip nano vim unzip --no-install-recommends -y
RUN apt-get install python3 python3-pip python3-wheel --no-install-recommends -y

# Add Ubuntu test ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test -y -n

# Add llvm key
RUN wget --progress=dot:giga -O - https://apt.llvm.org/llvm-snapshot.gpg.key | gpg --dearmour -o /usr/share/keyrings/llvm.gpg

# Add llvm apt repositories
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic main" >>"/etc/apt/sources.list.d/llvm.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-18 main" >>"/etc/apt/sources.list.d/llvm-18.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-17 main" >>"/etc/apt/sources.list.d/llvm-17.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-16 main" >>"/etc/apt/sources.list.d/llvm-16.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-15 main" >>"/etc/apt/sources.list.d/llvm-15.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-14 main" >>"/etc/apt/sources.list.d/llvm-14.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-13 main" >>"/etc/apt/sources.list.d/llvm-13.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-12 main" >>"/etc/apt/sources.list.d/llvm-12.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-11 main" >>"/etc/apt/sources.list.d/llvm-11.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-10 main" >>"/etc/apt/sources.list.d/llvm-10.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-9 main" >>"/etc/apt/sources.list.d/llvm-9.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-8 main" >>"/etc/apt/sources.list.d/llvm-8.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-7 main" >>"/etc/apt/sources.list.d/llvm-7.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-6.0 main" >>"/etc/apt/sources.list.d/llvm-6.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/bionic/ llvm-toolchain-bionic-5.0 main" >>"/etc/apt/sources.list.d/llvm-5.list"

# Update apt with new llvm packages
RUN apt-get update

# Install C++ packages
RUN apt-get install gcc gcc-11 gcc-10 gcc-9 gcc-8 gcc-7 gcc-6 gcc-5 --no-install-recommends -y
RUN apt-get install gcc-multilib gcc-11-multilib gcc-10-multilib gcc-9-multilib gcc-8-multilib gcc-7-multilib gcc-6-multilib gcc-5-multilib --no-install-recommends -y
RUN apt-get install g++ g++-11 g++-10 g++-9 g++-8 g++-7 g++-6 g++-5 --no-install-recommends -y
RUN apt-get install g++-multilib g++-11-multilib g++-10-multilib g++-9-multilib g++-8-multilib g++-7-multilib g++-6-multilib g++-5-multilib --no-install-recommends -y
RUN apt-get install clang clang-* --no-install-recommends -y
RUN apt-get install lld lld-* --no-install-recommends -y
RUN apt-get install libclang-rt-*-dev --no-install-recommends -y
RUN apt-get install llvm-runtime llvm-*-runtime --no-install-recommends -y
RUN apt-get install clang-tidy clang-tidy-18 --no-install-recommends -y
RUN apt-get install clang-format clang-format-18 --no-install-recommends -y
RUN apt-get install clang-tools clang-tools-18 --no-install-recommends -y
RUN apt-get install libc++1 --no-install-recommends -y
RUN apt-get install libc++abi1 --no-install-recommends -y
RUN apt-get install cmake cmake-curses-gui cppcheck iwyu ccache gdb ninja-build --no-install-recommends -y

# Install python packages
RUN pip3 --no-cache-dir install setuptools
RUN apt-get install libxml2 libxslt-dev python3-dev --no-install-recommends -y
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
