ARG build_at

FROM ubuntu:22.04
WORKDIR /tmp

ENV DEBIAN_FRONTEND=noninteractive
ENV build_at=${build_at}

RUN set -x && apt-get update && apt-get upgrade -y
RUN set -x && apt-get install -y man
RUN set -x && apt-get install -y unzip unar file
RUN set -x && apt-get install -y make gcc
RUN set -x && apt-get install -y wget curl git
RUN set -x && apt-get install -y xz-utils
RUN set -x && apt-get install -y jq
RUN set -x && apt-get install -y iproute2 net-tools
RUN set -x && apt-get install -y vim
RUN set -x && apt-get install -y less
RUN set -x && apt-get install -y rsync
RUN set -x && apt-get install -y rename
RUN set -x && apt-get install -y apt-utils
RUN set -x && apt-get install -y tcpdump
RUN set -x && apt-get install -y cifs-utils
RUN set -x && apt-get install -y libheif-examples
RUN set -x && apt-get install -y ffmpeg
RUN set -x && apt-get install -y libavif-*
RUN set -x && apt-get install -y libavif13
RUN set -x && apt-get install -y inkscape
RUN set -x && apt-get install -y fcrackzip
RUN set -x && apt-get install -y locales && localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG=ja_JP.UTF-8
ENV LANGUAGE=ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8
ENV TZ=JST-9
ENV TERM=xterm

RUN set -x && apt-get install -y language-pack-ja-base language-pack-ja ibus-mozc && \
	update-locale LANG=ja_JP.UTF-8 LANGUAGE="ja_JP:ja"

RUN echo '' >> /etc/bashrc ; \
	echo '# Custom command' >> /etc/bashrc ;\
	echo "alias ls='ls --color=auto'" >> /etc/bashrc ;\
	echo "alias ll='ls -lhA'" >> /etc/bashrc ;\
	echo '' >> /etc/bashrc

# https://rclone.org/install/
RUN set -x && curl -sS https://rclone.org/install.sh | bash

# yt-dlp
RUN set -x && curl -L https://github.com/yt-dlp/yt-dlp/releases/download/2025.01.26/yt-dlp -o /usr/local/bin/yt-dlp && chmod a+rx /usr/local/bin/yt-dlp

# scripts
COPY scripts/* /usr/bin/
RUN chmod -R a+x /usr/bin/

# cleanup
RUN set -x && apt-get autoremove -y
