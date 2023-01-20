FROM ubuntu

WORKDIR /app

RUN apt update
RUN apt install git make curl vim unzip -y
RUN curl -OL "https://go.dev/dl/go1.19.5.linux-amd64.tar.gz"
RUN tar -xvf go1.19.5.linux-amd64.tar.gz -C /usr/bin
RUN curl -OL "https://github.com/protocolbuffers/protobuf/releases/download/v21.12/protoc-21.12-linux-x86_64.zip"
RUN unzip protoc-21.12-linux-x86_64.zip
RUN mkdir -p usr/local/bin 
RUN mv bin/protoc /usr/local/bin
RUN rm -rf bin include && rm readme.txt
# RUN touch $HOME/.bashrc
RUN echo "export path=\$PATH:/usr/bin/go" >> $HOME/.bashrc && \
    echo "export path=\$PATH:/usr/local/bin" >> $HOME/.bashrc && \
    echo "alias sou='source ~/.bashrc'" >> $HOME/.bashrc 
RUN . $HOME/.bashrc

RUN git clone "https://github.com/cbot918/experiment"
RUN /usr/bin/go/bin/go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
RUN /usr/bin/go/bin/go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2


