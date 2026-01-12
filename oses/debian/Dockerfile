FROM        --platform=$TARGETOS/$TARGETARCH debian:bookworm-slim

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

LABEL       org.opencontainers.image.source="https://github.com/pyrodactyl-oss/images"

RUN apt update && apt upgrade -y \
	&& apt install -y \
	gcc g++ libgcc1 libc++-dev gdb libc6 git wget curl tar zip unzip \
	binutils xz-utils liblzo2-2 cabextract iproute2 net-tools \
	netcat-openbsd telnet libatomic1 libsdl1.2debian libsdl2-2.0-0 \
	libfontconfig1 libicu72 icu-devtools libunwind8 libssl-dev sqlite3 \
	libsqlite3-dev libmariadb-dev libduktape207 locales ffmpeg gnupg2 \
	apt-transport-https software-properties-common ca-certificates tzdata \
	liblua5.3-0 liblua5.3-dev libz-dev rapidjson-dev \
	&& rm -rf /var/lib/apt/lists/* \
	&& sed -i '/en_US.UTF-8/s/^# //g' /etc/locale.gen \
	&& locale-gen en_US.UTF-8 \
	&& update-locale LANG=en_US.UTF-8 \
	&& dpkg-reconfigure --frontend noninteractive locales \
	&& useradd -m -d /home/container -s /bin/bash container


USER        container
ENV         USER=container HOME=/home/container
ENV         DEBIAN_FRONTEND=noninteractive

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
