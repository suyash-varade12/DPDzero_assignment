#pull the image of golang official
FROM golang:1.20

#set working directory
WORKDIR /app

#copy files local to cotainer
COPY . .

#initialize a go module and build
RUN go mod init app && go build -o main .

#expose port
EXPOSE 8001


CMD ["./main"]