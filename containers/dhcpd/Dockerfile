FROM alpine:3.18@sha256:82d1e9d7ed48a7523bdebc18cf6290bdb97b82302a8a9c27d4fe885949ea94d1

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