# build container stage 1
FROM docker.io/library/golang:1.15.15-alpine3.14
WORKDIR /src
COPY hello.go .
#RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o bin/app .
RUN CGO_ENABLED=0 GOOS=linux go build hello.go && mkdir bin && mv hello ./bin/hello
# app container stage 2
FROM docker.io/library/alpine:3.12.4
COPY --from=0 /src/bin/hello hello
ENV SUN_CIPHER_ID=5b9c1065-e39d-4a43-a04a-e59bcea3e03f
CMD ["./hello"]
