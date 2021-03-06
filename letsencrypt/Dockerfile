ARG BUILD_FROM
FROM $BUILD_FROM

# setup base
ARG CERTBOT_VERSION
ARG CERTBOT_NETCUP_VERSION
ARG CERTBOT_GANDI_VERSION
ARG CERTBOT_DNS_TRANSIP_VERSION

RUN apk add --no-cache --update \
        libffi \
        musl \
        openssl \
    && apk add --no-cache --virtual .build-dependencies \
        g++ \
        libffi-dev \
        musl-dev \
        openssl-dev \
    && pip3 install --no-cache-dir --find-links \
        "https://wheels.home-assistant.io/alpine-$(cut -d '.' -f 1-2 < /etc/alpine-release)/${BUILD_ARCH}/" \
        certbot==${CERTBOT_VERSION} \
        certbot-dns-cloudflare==${CERTBOT_VERSION} \
        certbot-dns-cloudxns==${CERTBOT_VERSION} \
        certbot-dns-digitalocean==${CERTBOT_VERSION} \
        certbot-dns-dnsimple==${CERTBOT_VERSION} \
        certbot-dns-dnsmadeeasy==${CERTBOT_VERSION} \
        certbot-dns-gehirn==${CERTBOT_VERSION} \
        certbot-dns-google==${CERTBOT_VERSION} \
        certbot-dns-linode==${CERTBOT_VERSION} \
        certbot-dns-luadns==${CERTBOT_VERSION} \
        certbot-dns-nsone==${CERTBOT_VERSION} \
        certbot-dns-ovh==${CERTBOT_VERSION} \
        certbot-dns-rfc2136==${CERTBOT_VERSION} \
        certbot-dns-route53==${CERTBOT_VERSION} \
        certbot-dns-sakuracloud==${CERTBOT_VERSION} \
        certbot-dns-netcup==${CERTBOT_NETCUP_VERSION} \
        certbot-plugin-gandi==${CERTBOT_GANDI_VERSION} \
        certbot-dns-transip==${CERTBOT_DNS_TRANSIP_VERSION} \
    && apk del .build-dependencies

# Copy data
COPY rootfs /
