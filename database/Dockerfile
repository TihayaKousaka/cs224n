
FROM rust:1.67.0-bullseye as builder

LABEL org.opencontainers.image.title="ai4db"
LABEL maintainer="ai4db <makonohanain@gmail.com>"
LABEL org.opencontainers.image.vendor="Cloudnatively Pvt Ltd"
LABEL org.opencontainers.image.licenses="AGPL-3.0"

WORKDIR /parseable
COPY . .
RUN cargo build --release

# final stage
FROM gcr.io/distroless/cc-debian11:latest

WORKDIR /ai4db

COPY --from=builder /parseable/target/release/ai4db /usr/bin/ai4db

CMD ["parseable"]
