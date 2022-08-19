FROM eerikas/ego:1.0.1
WORKDIR /server
COPY . .
RUN ego-go build -o server
RUN ego sign
CMD [ "ego", "run", "server" ]
# ENTRYPOINT ["tail", "-f", "/dev/null"]