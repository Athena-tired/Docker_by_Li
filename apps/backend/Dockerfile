FROM gcc:13-bookworm AS build
WORKDIR /src
COPY . .
RUN make -C lib
RUN make -C apps/backend

FROM debian:bookworm-slim
COPY --from=build /src/apps/backend/backend /usr/local/bin/backend
EXPOSE 9000
ENTRYPOINT ["/usr/local/bin/backend"]
