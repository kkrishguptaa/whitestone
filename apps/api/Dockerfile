FROM golang:1.25.6-alpine@sha256:d9b2e14101f27ec8d09674cd01186798d227bb0daec90e032aeb1cd22ac0f029 AS builder

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

# Copy source code
COPY . .

RUN go build -o app .

FROM alpine:latest@sha256:865b95f46d98cf867a156fe4a135ad3fe50d2056aa3f25ed31662dff6da4eb62

WORKDIR /app

COPY --from=builder /app/app .

EXPOSE ${API_PORT:-8080}

CMD ["./app"]
