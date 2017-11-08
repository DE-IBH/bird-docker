FROM debian:stretch-slim

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y bird && mkdir /run/bird

COPY ./check_bird4 /usr/local/bin/check_bird

ENTRYPOINT ["/usr/sbin/bird", "-f"]
CMD []
