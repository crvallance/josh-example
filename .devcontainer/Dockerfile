FROM ubuntu:kinetic-20230217

# Install all the pre-reqs and niceties
RUN apt update && apt install -y build-essential libssl-dev zlib1g-dev yasm \
    libgmp-dev libpcap-dev pkg-config libbz2-dev wget git libusb-1.0-0-dev \
    bash-completion

# Download source and compile.
# This is stolen from the john repo's docker instructions
RUN git clone --depth 10 https://github.com/openwall/john.git && \
    cd john/src && ./configure --disable-native-tests \
    --disable-openmp --enable-simd=sse2 && make -s clean \
    && make -sj2 && make install

# Setup some path stuff to make execution easier in bash environment
RUN echo "alias john=/john/run/john" >> /root/.bashrc && \
    echo "source /john/run/john.bash_completion" >> /root/.bashrc

# Cleanup apt, after all this is in a container
RUN apt clean autoclean && apt autoremove --yes