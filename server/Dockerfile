FROM golang:1.23-alpine3.20 AS base

WORKDIR /app

COPY go.mod ./

RUN go mod download && go mod verify

COPY . .

RUN go build -v -o main .

FROM base AS MIGRATION
CMD [ "go", "run", "./consumer/database/migration/run/main.go" ]

FROM base AS test
CMD ["go", "test", "./..."]

FROM base AS production
CMD ["/app/main"]