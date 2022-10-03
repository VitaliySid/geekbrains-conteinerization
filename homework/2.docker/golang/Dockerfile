
FROM golang:1.18-buster as builder

WORKDIR /app

COPY . .

RUN go mod download
RUN go mod verify

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o srv main.go

FROM alpine:3.16

COPY --from=builder /app/srv /

EXPOSE 8080

CMD [ "/srv" ]
