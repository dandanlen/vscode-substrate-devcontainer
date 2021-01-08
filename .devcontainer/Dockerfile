# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.145.1/containers/rust/.devcontainer/base.Dockerfile

FROM mcr.microsoft.com/vscode/devcontainers/rust:0-1

# Substrate-compatible Rust version.
ARG RUST_VERSION=nightly-2020-10-05
RUN rustup install $RUST_VERSION \
    && rustup update \
    && rustup default $RUST_VERSION \
    && rustup component add rls rust-analysis rust-src clippy rustfmt llvm-tools-preview \
    && rustup target add wasm32-unknown-unknown --toolchain $RUST_VERSION

# Install some subtrate tools.
# RUN cargo install --force --git https://github.com/alexcrichton/wasm-gc \
#     && cargo install substrate-deps \
#     && cargo install diener

# Substrate and rust comiler dependencies.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        cmake \
        build-essential \
        clang \
        libclang-dev \
        lld

# Node, npm and yarn for front-end stuff.
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs
RUN npm install -g yarn

# Remove unnecessary packages.
RUN apt -y autoremove
