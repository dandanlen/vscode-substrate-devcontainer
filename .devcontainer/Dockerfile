# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.145.1/containers/rust/.devcontainer/base.Dockerfile

FROM mcr.microsoft.com/vscode/devcontainers/rust:0-1

# Substrate-compatible Rust version.
ARG RUST_VERSION=nightly
RUN rustup install $RUST_VERSION \
    && rustup update \
    && rustup default $RUST_VERSION \
    && rustup component add rls rust-analysis rust-src clippy rustfmt llvm-tools-preview \
    && rustup target add wasm32-unknown-unknown --toolchain $RUST_VERSION

# Install some subtrate tools.
# RUN cargo install --force --git https://github.com/alexcrichton/wasm-gc \
#     && cargo install substrate-deps \
#     && cargo install diener

# Substrate and rust compiler dependencies.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        cmake \
        build-essential \
        clang \
        libclang-dev \
        lld

# Install sccache for cached builds
RUN cargo install sccache
ENV RUSTC_WRAPPER=sccache

# Node, npm and yarn for front-end stuff.
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

# Remove unnecessary packages.
RUN apt -y autoremove
