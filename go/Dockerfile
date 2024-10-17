FROM golang:1.23 AS base

WORKDIR /usr/src/app

COPY . .
RUN go mod download && go mod verify

RUN CGO_ENABLED=0 go build -ldflags="-s -w" -o app .

FROM scratch
WORKDIR /usr/src/app

COPY --from=base /usr/src/app .

CMD [ "./app" ]
