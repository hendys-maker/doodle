<<<<<<< HEAD:birthday2019/Dockerfile
FROM golang:1.11-alpine AS builder
=======
FROM --platform=$BUILDPLATFORM golang:1.11-alpine AS builder
>>>>>>> multiplatform:Dockerfile
RUN apk add --no-cache git
RUN go get github.com/pdevine/go-asciisprite
WORKDIR /project
COPY surprise.go .
<<<<<<< HEAD:birthday2019/Dockerfile
RUN CGO_ENABLED=0 GOOS=linux go build -a -ldflags '-extldflags "-static"' -o surprise surprise.go
=======
>>>>>>> multiplatform:Dockerfile

ARG TARGETOS
ARG TARGETARCH
ENV GOOS=$TARGETOS GOARCH=$TARGETARCH
RUN CGO_ENABLED=0 go build -a -ldflags '-extldflags "-static"' -o surprise surprise.go

FROM scratch AS release-linux
COPY --from=builder /project/surprise /surprise
ENTRYPOINT ["/surprise"]
<<<<<<< HEAD:birthday2019/Dockerfile
=======

FROM microsoft/nanoserver AS release-windows
COPY --from=builder /project/surprise /surprise.exe
ENTRYPOINT ["\\surprise.exe"]

FROM release-$TARGETOS
>>>>>>> multiplatform:Dockerfile
