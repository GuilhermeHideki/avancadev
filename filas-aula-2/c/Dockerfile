FROM golang:1.15 as builder

WORKDIR /go/src/microservice
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -a -o /go/app/microservice

FROM alpine:3.12
COPY --from=builder /go/app/microservice ./
ENTRYPOINT ["./microservice"]
