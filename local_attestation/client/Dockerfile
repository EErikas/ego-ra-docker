FROM eerikas/ego:1.0.1
WORKDIR /client
COPY . .
RUN ego-go build -o client
RUN ego sign
CMD [ "ego", "run", "client" ]
