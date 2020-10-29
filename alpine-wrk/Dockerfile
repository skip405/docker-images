FROM alpine

RUN apk add --update alpine-sdk perl linux-headers;

RUN git clone https://github.com/wg/wrk.git wrk; \
    cd wrk; \
    make; \
    cp wrk /usr/local/bin