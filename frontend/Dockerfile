FROM golang:1.16 AS builder

WORKDIR /app

COPY go.mod ./
RUN go mod download

COPY . .

RUN go build -o frontend .

FROM alpine:3.22

WORKDIR /app

COPY --from=builder /app/frontend .

EXPOSE 8080

CMD ["./frontend"]