FROM registry.cn-hangzhou.aliyuncs.com/knative-sample/golang:1.12 as builder
#WORKDIR /go/src/alibaba.com/tianshu/k8s-manager
WORKDIR /go/src/github.com/knative-sample/revision-controller
COPY cmd/ cmd
COPY pkg/ pkg
COPY vendor/ vendor
RUN CGO_ENABLED=0 go build -o controller cmd/main.go

FROM registry.cn-hangzhou.aliyuncs.com/knative-sample/alpine-sh:3.9
COPY --from=builder /go/src/github.com/knative-sample/revision-controller /app/bin/
ENTRYPOINT ["/app/bin/controller"]
