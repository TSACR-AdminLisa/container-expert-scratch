#? compilacion/build SDK
FROM golang:1.14.3 AS builder

WORKDIR /compose/main

COPY . ./
COPY main.go main.go
RUN CGO_ENABLED=0 go build -o backend main.go


#* Multi stage builds
FROM alpine:3 AS release
EXPOSE 8080
COPY --from=builder /compose/main/backend /usr/local/bin/backend
ENTRYPOINT  ["/usr/local/bin/backend"]
