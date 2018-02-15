FROM golang:1.8
MAINTAINER Janusz Nowakowski <jnowakowski@gmail.com>

EXPOSE 9735 10009
ENV GODEBUG netdns=cgo

RUN go get -u github.com/Masterminds/glide
RUN git clone https://github.com/lightningnetwork/lnd $GOPATH/src/github.com/lightningnetwork/lnd
WORKDIR $GOPATH/src/github.com/lightningnetwork/lnd
RUN glide install
RUN go install . ./cmd/...

COPY "start-lnd.sh" .
RUN chmod +x start-lnd.sh

CMD ["lnd", "--noencryptwallet", "--bitcoin.active", "--bitcoin.testnet", "--debuglevel=info", "--bitcoin.node=neutrino", "--neutrino.connect=faucet.lightning.community"]

