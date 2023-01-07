FROM ubuntu:20.04

# Update apt
RUN apt-get update && apt-get upgrade -y

# Install basic utilities
RUN DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC \
    apt-get install build-essential git wget sudo grep software-properties-common gpg gnupg gpg-agent tar curl zip unzip nano vim fzf --no-install-recommends -y
RUN apt-get install python3 python-is-python3 python3-pip python3-wheel --no-install-recommends -y

# Add Ubuntu test ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test -y -n

# Add llvm key
RUN wget --progress=dot:giga -O - https://apt.llvm.org/llvm-snapshot.gpg.key | gpg --dearmour -o /usr/share/keyrings/llvm.gpg

# Add llvm apt repositories
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal main" >> "/etc/apt/sources.list.d/llvm.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal-15 main" >> "/etc/apt/sources.list.d/llvm-15.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal-14 main" >> "/etc/apt/sources.list.d/llvm-14.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal-13 main" >> "/etc/apt/sources.list.d/llvm-13.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal-12 main" >> "/etc/apt/sources.list.d/llvm-12.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal-11 main" >> "/etc/apt/sources.list.d/llvm-11.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal-10 main" >> "/etc/apt/sources.list.d/llvm-10.list"
RUN echo "deb [signed-by=/usr/share/keyrings/llvm.gpg] https://apt.llvm.org/focal/ llvm-toolchain-focal-9 main" >> "/etc/apt/sources.list.d/llvm-9.list"

# Update apt with new llvm packages
RUN apt-get update

# Install C++ packages
RUN apt-get install gcc gcc-11 gcc-10 gcc-9 gcc-8 gcc-7 --no-install-recommends -y
RUN apt-get install gcc-multilib gcc-11-multilib gcc-10-multilib gcc-9-multilib gcc-8-multilib gcc-7-multilib --no-install-recommends -y
RUN apt-get install g++ g++-11 g++-10 g++-9 g++-8 g++-7 --no-install-recommends -y
RUN apt-get install g++-multilib g++-11-multilib g++-10-multilib g++-9-multilib g++-8-multilib g++-7-multilib --no-install-recommends -y
RUN apt-get install clang clang-15 clang-14 clang-13 clang-12 clang-11 clang-10 clang-9 clang-8 clang-7 --no-install-recommends -y
RUN apt-get install lld lld-15 lld-14 lld-13 lld-12 lld-11 lld-10 lld-9 lld-8 lld-7 --no-install-recommends -y
RUN apt-get install clang-tidy clang-tidy-15 --no-install-recommends -y
RUN apt-get install clang-format clang-format-15 --no-install-recommends -y
RUN apt-get install clang-tools clang-tools-15 --no-install-recommends -y
RUN apt-get install libc++1 --no-install-recommends -y
RUN apt-get install libc++abi1 --no-install-recommends -y
RUN apt-get install cmake cppcheck iwyu ccache gdb ninja-build --no-install-recommends -y

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