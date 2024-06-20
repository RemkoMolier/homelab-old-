FROM alpine:3.20@sha256:b89d9c93e9ed3597455c90a0b88a8bbb5cb7188438f70953fede212a0c4394e0

# renovate: datasource=repology depName=alpine_3_18/dhcp versioning=loose
ARG DHCP_VERSION="4.4.3_p1-r2"

RUN apk add --no-cache \
        dhcp-server-vanilla="${DHCP_VERSION}" && \
    touch /var/lib/dhcp/dhcpd.leases && \
    chown dhcp:dhcp /var/lib/dhcp/dhcpd.leases

EXPOSE 67/udp 67/tcp 
VOLUME /etc/dhcp

USER dhcp

HEALTHCHECK NONE

ENTRYPOINT [ "/usr/sbin/dhcpd" ]
CMD [ "-4", "-f", "-d", "--no-pid", "-cf", "/etc/dhcp/dhcpd.conf" ]