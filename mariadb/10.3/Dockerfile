# -----------------------------------------------------
# MariaDB Image for Pterodactyl
# -----------------------------------------------------
FROM        --platform=$TARGETOS/$TARGETARCH mariadb:10.3

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

ENV         DEBIAN_FRONTEND noninteractive

RUN         apt update -y \
            && apt install -y netcat \
            && useradd -d /home/container -m container -s /bin/bash
RUN 		sed -i "s/skip-name-resolve//" /etc/mysql/my.cnf
RUN 		sed -i "s/skip-name-resolve//" /etc/mysql/mariadb.cnf
RUN 		sed -i "s/skip-name-resolve//" /etc/mysql/debian.cnf
RUN 		sed -i "s/skip-name-resolve//" /etc/mysql/mariadb.conf.d/05-skipcache.cnf

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
