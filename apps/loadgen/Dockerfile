# Этап 1: сборка
FROM gcc:13-bookworm AS build
WORKDIR /src
COPY . .
RUN make -C lib
RUN make -C apps/loadgen

# Этап 2: минимальный образ запуска
FROM debian:bookworm-slim
COPY --from=build /src/apps/loadgen/loadgen /usr/local/bin/loadgen
ENTRYPOINT ["/usr/local/bin/loadgen"]
