FROM fuzzers/cargo-fuzz:0.10.0 as builder

ADD . /tokei
WORKDIR /tokei
RUN rustup toolchain install nightly
WORKDIR /tokei/fuzz
RUN RUSTFLAGS="-Znew-llvm-pass-manager=no" cargo +nightly fuzz build

FROM ubuntu:20.04
COPY --from=builder /tokei/fuzz/target/x86_64-unknown-linux-gnu/release /
