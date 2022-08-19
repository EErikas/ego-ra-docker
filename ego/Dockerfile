FROM ubuntu:focal
ENV DEBIAN_FRONTEND=noninteractive 

WORKDIR /server

# Getting essentials up and running:
RUN apt update -y && apt upgrade -y 
RUN apt install git wget gnupg2 lsb-release software-properties-common build-essential libssl-dev -y
RUN apt clean all -y

# Installing SGX drivers: 
RUN wget -qO- https://download.01.org/intel-sgx/sgx_repo/ubuntu/intel-sgx-deb.key | apt-key add
RUN add-apt-repository "deb [arch=amd64] https://download.01.org/intel-sgx/sgx_repo/ubuntu `lsb_release -cs` main" -y

# Setup EGo:
ARG VERSION=1.0.1
ENV OE_SIMULATION=0

RUN wget https://github.com/edgelesssys/ego/releases/download/v${VERSION}/ego_${VERSION}_amd64.deb
RUN apt install ./ego_${VERSION}_amd64.deb -y

RUN rm ego_${VERSION}_amd64.deb
# Setup PCCS
# RUN ego install libsgx-dcap-default-qpl

# RUN if [[ -e /usr/share/doc/az-dcap-client ]]; then apt remove -y az-dcap-client; fi
# RUN apt install -y libsgx-dcap-default-qpl
# RUN ln -s /usr/lib/x86_64-linux-gnu/libdcap_quoteprov.so.1 /usr/lib/x86_64-linux-gnu/libdcap_quoteprov.so
# # RUN sed -i 's/"use_secure_cert": true/"use_secure_cert": false/g' /etc/sgx_default_qcnl.conf
# # RUN sed -i 's/"pccs_url":https://localhost:8081/sgx/certification/v3/"/"pccs_url": "https://${PCCS}:8081/sgx/certification/v3/"/g' /etc/sgx_default_qcnl.conf

# COPY ./sgx_default_qcnl.conf /etc/sgx_default_qcnl.conf

# RUN cat /etc/sgx_default_qcnl.conf
# # Build go-tunnel
# WORKDIR /server

# COPY ./remote_attestation/ .
# # RUN make enclave
# # WORKDIR /server/go-tunnel/bin/enclave

# # ENV OE_SIMULATION=1
# RUN ego-go build
# RUN ego sign server
# CMD ["ego", "run", "server"]
# # CMD [ "ego", "run", "gotun", "server.conf" ]