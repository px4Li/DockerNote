FROM gcc:9.4 AS builder
COPY hello.cpp /src/hello.cpp
WORKDIR /src
RUN g++ --static hello.cpp -o hello


FROM alpine:3.13.5
COPY --from=builder /src/hello /src/hello
ENTRYPOINT ["/src/hello"]
CMD []