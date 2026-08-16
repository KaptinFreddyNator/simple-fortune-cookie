FROM golang:1.16 AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN CGO_ENABLED=0 go build -o backend .

FROM alpine:3.22

WORKDIR /app

COPY --from=builder /app/backend .

EXPOSE 9000

CMD ["./backend"]