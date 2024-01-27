FROM alpine:3.18@sha256:11e21d7b981a59554b3f822c49f6e9f57b6068bb74f49c4cd5cc4c663c7e5160

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