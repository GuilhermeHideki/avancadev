FROM golang:1.15 as builder

WORKDIR /go/src/microservice
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -a -o /go/app/microservice

FROM alpine:3.12
COPY --from=builder /go/app/microservice ./
COPY --from=builder /go/src/microservice/templates ./templates
EXPOSE 9090
ENTRYPOINT ["./microservice"]
