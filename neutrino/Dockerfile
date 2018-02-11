FROM golang

WORKDIR /go/src/app

RUN export GOPATH=~/gocode
RUN export PATH=$PATH:$GOPATH/bin

RUN go get -u github.com/Masterminds/glide 

RUN git clone https://github.com/lightningnetwork/lnd $GOPATH/src/github.com/lightningnetwork/lnd

RUN cd $GOPATH/src/github.com/lightningnetwork/lnd && glide install && go install . ./cmd/...

RUN git clone https://github.com/roasbeef/btcd $GOPATH/src/github.com/roasbeef/btcd

RUN cd $GOPATH/src/github.com/roasbeef/btcd && glide install && go install . ./cmd/...

CMD ["lnd", "--noencryptwallet", "--bitcoin.active", "--bitcoin.testnet", "--debuglevel=info", "--bitcoin.node=neutrino", "--neutrino.connect=faucet.lightning.community"]

