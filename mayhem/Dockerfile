FROM fuzzers/cargo-fuzz:0.10.0

ADD . /tokei
WORKDIR /tokei
RUN rustup toolchain install nightly
WORKDIR /tokei/fuzz
RUN RUSTFLAGS="-Znew-llvm-pass-manager=no" cargo +nightly fuzz build

# Set to fuzz!
ENTRYPOINT []
CMD ["/tokei/fuzz/target/x86_64-unknown-linux-gnu/release/parse_from_slice_panic"]
