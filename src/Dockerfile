# Build stage
FROM golang:1.20-alpine3.16 AS builder
WORKDIR /app
COPY . .
RUN go build -o main ./main.go

# Run stage
FROM alpine:3.16
RUN apk add ca-certificates

COPY --from=builder /app/main /usr/local/bin/
RUN adduser -D -g 'app' app

EXPOSE 8080

USER app:app
CMD [ "/usr/local/bin/main" ]