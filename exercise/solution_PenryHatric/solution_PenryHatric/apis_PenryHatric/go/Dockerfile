FROM golang:latest AS builder

WORKDIR /app

COPY . .

RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -o calculator main.go

FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/calculator .

EXPOSE 5000:8989

CMD ["/app/calculator"]
