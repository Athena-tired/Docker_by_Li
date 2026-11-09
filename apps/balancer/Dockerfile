FROM gcc:13-bookworm AS build
WORKDIR /src
COPY . .
RUN make -C lib
RUN make -C apps/balancer

FROM debian:bookworm-slim
COPY --from=build /src/apps/balancer/balancer /usr/local/bin/balancer
EXPOSE 8080
ENTRYPOINT ["/usr/local/bin/balancer"]
