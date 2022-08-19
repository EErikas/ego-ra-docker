FROM eerikas/ego:1.0.1
WORKDIR /workdir
COPY . .
RUN cd server && ego-go build && ego sign
RUN cd client && ego-go build && ego sign