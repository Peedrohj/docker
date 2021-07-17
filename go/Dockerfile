
# Build a executable file
FROM golang:rc-alpine as builder

WORKDIR $GOPATH/src/codeeducation/app/

RUN go mod init

COPY /code .
RUN GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o /go/bin/main

# Build a small image to run executable file
FROM scratch  

WORKDIR /root/

COPY --from=builder /go/bin/main .
CMD ["./main"]
