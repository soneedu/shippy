build:
	protoc -I . --go_out=plugins=micro:$(GOPATH)/src/shippy/user-service proto/user/user.proto
	CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build
	docker build -t user-service .

run:
	docker run -p 50053:50051 -e MICRO_SERVER_ADDRESS=:50051 -e MICRO_REGISTRY=mdns -e DB_NAME=postgres -e DB_HOST=172.17.0.1 -e DB_PORT=5432 -e DB_USER=postgres -e DB_PASSWORD=postgres  user-service

#	docker run -p 50053:50051 -e MICRO_SERVER_ADDRESS=:50051 -e MICRO_REGISTRY=mdns  user-service
