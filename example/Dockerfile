ARG BUILD_FROM=hassioaddons/base:2.3.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Set workdir
WORKDIR /opt

# Copy root filesystem
COPY rootfs /


# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Setup base
RUN apk add --no-cache \
        coreutils=8.29-r2 \
        wget=1.19.5-r0 \
    && apk add --no-cache \
        apk-tools=2.10.1-r0 \
        bash=4.4.19-r1 \
        busybox=1.28.4-r1 \
        ca-certificates=20171114-r3 \
        curl=7.61.1-r1 \
        jq=1.6_rc1-r1 \
        musl-utils=1.1.19-r10 \
        musl=1.1.19-r10 \
        tzdata=2018f-r0    
        
    #      \
    # && mkdir -p /etc/fix-attrs.d \
    # && mkdir -p /etc/services.d \
    # && apk del --purge .build-dependencies 

# Entrypoint & CMD (copied from add-on base)
ENTRYPOINT ["/init"]

# Build arugments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Example" \
    io.hass.description="Example add-on by Community Hass.io Add-ons" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Franck Nijhof <frenck@addons.community>" \
    org.label-schema.description="Example add-on by Community Hass.io Add-ons" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Example" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://addons.community" \
    org.label-schema.usage="https://github.com/hassio-addons/addon-example/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/hassio-addons/addon-example" \
    org.label-schema.vendor="Community Hass.io Addons"
