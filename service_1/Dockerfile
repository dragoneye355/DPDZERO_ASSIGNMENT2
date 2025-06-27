# ---------- Stage 1: Build ----------
FROM golang:1.22-alpine AS builder

WORKDIR /app

# Copy the Go source file
COPY main.go .

# Build the Go app
RUN go build -o service1 main.go

# ---------- Stage 2: Runtime ----------
FROM alpine:latest

WORKDIR /app

# Copy the built binary from builder
COPY --from=builder /app/service1 .

# Expose the port your Go app uses
EXPOSE 8001

# Run the Go service
CMD ["./service1"]
