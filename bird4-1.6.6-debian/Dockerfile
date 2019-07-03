FROM debian:buster-slim

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y bird && mkdir /run/bird

ENTRYPOINT ["/usr/sbin/bird", "-f"]
CMD []
