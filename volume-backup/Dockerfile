# syntax=docker/dockerfile:1

FROM alpine:3

WORKDIR /script

RUN apk add -u --no-cache \
    dumb-init bash docker curl xz tar pigz zstd

ADD --link --chown=0:0 --chmod=775 \
    # https://github.com/loomchild/volume-backup/blob/d31abfbdae62c68e619b629d9769c9f13944e7cd/volume-backup.sh
    https://raw.githubusercontent.com/loomchild/volume-backup/d31abfbdae62c68e619b629d9769c9f13944e7cd/volume-backup.sh .
ADD --link --chown=0:0 --chmod=775 \
    # MIT
    # https://github.com/loomchild/volume-backup/blob/d31abfbdae62c68e619b629d9769c9f13944e7cd/LICENSE
    https://raw.githubusercontent.com/loomchild/volume-backup/d31abfbdae62c68e619b629d9769c9f13944e7cd/LICENSE /licenses/volume-backup.LICENSE

COPY --link --chown=0:0 --chmod=775 \
    script/* .
# MIT
COPY --chmod=775 LICENSE /licenses/LICENSE

# This docker image is designed to be executed with root privileges in order to handle volume files with any permissions.
USER 0
VOLUME [ "/volume", "/backup" ]

ENTRYPOINT [ "dumb-init", "--" ]
CMD [ "./volume-backup.sh", "-h" ]