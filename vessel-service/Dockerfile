# vessel-service/Dockerfile
FROM golang as builder

RUN apt-get install git -y

WORKDIR /app/shippy-service-vessel

COPY . .

RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o shippy-service-vessel


FROM debian:latest

RUN mkdir /app
WORKDIR /app
COPY --from=builder /app/shippy-service-vessel .

CMD ["./shippy-service-vessel"]