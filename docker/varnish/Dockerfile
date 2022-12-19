FROM varnish:7.2.1-alpine
USER root
ENV VARNISH_VERSION 7.2

RUN BASE_PKGS="py3-docutils python3 autoconf make automake libtool git"; \
    apk add --virtual varnish-build-deps -q --no-progress --update $BASE_PKGS \
    # Installing vmods
    && cd /tmp && git clone https://github.com/nigoroll/libvmod-dynamic && cd libvmod-dynamic \
    &&  git checkout ${VARNISH_VERSION} \
    && ./autogen.sh && ./configure && make install clean \
    # cleanup
    && apk del --no-network varnish-build-deps;

RUN apk add --no-cache bash
