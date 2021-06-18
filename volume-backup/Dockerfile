FROM loomchild/volume-backup

RUN apk update && apk add --no-cache bash docker

WORKDIR /script
COPY . /

ENTRYPOINT [ "/usr/bin/dumb-init", "--" ]