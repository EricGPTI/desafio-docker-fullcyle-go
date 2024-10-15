FROM golang:1.23 AS base

WORKDIR /usr/src/app

COPY . .
RUN go mod download && go mod verify

RUN go build -o app .

FROM golang:1.23-alpine
WORKDIR /usr/src/app

COPY --from=base /usr/src/app .

EXPOSE 8888

CMD [ "go", "run", "app.go" ]
