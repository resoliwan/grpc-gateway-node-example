# Goal
Generate rest API for Grpc with node.

# Component
- Node server
- Grpc http proxy server
- curl client

# API
```
GET /hello
return hello
```
# Sequence flow
![flow](./doc/a.png)

# Source from
- https://github.com/grpc-ecosystem/grpc-gateway
- https://github.com/grpc/grpc

# Compile proto
- Optional (It repository already include compiled file)
```
protoc -I/usr/local/include -I. \
  -I$GOPATH/src \
  -I$GOPATH/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis \
  --grpc-gateway_out=logtostderr=true:./httpproxy \
  --go_out=plugins=grpc:./httpproxy \
  ./protos/helloworld.proto
```

# Install node package
```
cd node
npm install
```

# Test
### Run http proxy server (port: 8080)
```
go run httpproxy/server.go
```

### Run node js (port: 50051)
```
node node/greeter_server.js
```

### Run clinet
```
curl http://localhost:8080/hello
```

