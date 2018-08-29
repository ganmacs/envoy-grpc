FROM golang:1.10.3

ARG DEP_VERSION=v0.5.0
ARG DEP_SHA256=287b08291e14f1fae8ba44374b26a2b12eb941af3497ed0ca649253e21ba2f83
RUN curl -sSfLO https://github.com/golang/dep/releases/download/${DEP_VERSION}/dep-linux-amd64 && \
    echo "${DEP_SHA256} dep-linux-amd64" | sha256sum -c - && \
    mv dep-linux-amd64 /go/bin/dep && \
    chmod +x /go/bin/dep

WORKDIR /go/src/github.com/ganmacs/envoy-grpc/app2
COPY Gopkg.toml Gopkg.lock /go/src/github.com/ganmacs/envoy-grpc/app2/
RUN dep ensure -vendor-only

COPY . /go/src/github.com/ganmacs/envoy-grpc/app2
RUN go build -o grpc_server

EXPOSE 8000

CMD ["./grpc_server"]
