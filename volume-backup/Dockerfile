# syntax=docker/dockerfile:1

FROM alpine:3

WORKDIR /script

RUN apk add -u --no-cache \
    dumb-init bash docker curl xz tar pigz zstd

# https://github.com/loomchild/volume-backup/blob/master/volume-backup.sh
ADD --link --chown=0:0 --chmod=775 https://raw.githubusercontent.com/loomchild/volume-backup/master/volume-backup.sh .

COPY --link --chown=0:0 --chmod=775 \
    script/* .

# This docker image is designed to be executed with root privileges in order to handle volume files with any permissions.
USER 0
VOLUME [ "/volume", "/backup" ]

ENTRYPOINT [ "dumb-init", "--" ]
CMD [ "volume-backup.sh", "-h" ]