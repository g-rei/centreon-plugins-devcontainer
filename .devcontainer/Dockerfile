FROM debian:11
RUN apt-get update && apt-get -y upgrade
RUN apt-get -y install 'git' 'locales' 'gpg' 'wget' 'curl' 'lsb-release' 'libdatetime-perl' 'cpanminus' 'libcurl4-openssl-dev' 'build-essential'
RUN sed -i '/en_US.UTF-8/s/^# //g' /etc/locale.gen && \
    locale-gen
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
RUN echo "deb https://packages.centreon.com/apt-22.04-stable $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/centreon.list \
    wget -O- https://apt-key.centreon.com | gpg --dearmor | tee /etc/apt/trusted.gpg.d/centreon.gpg > /dev/null 2>&1   
RUN apt-get -y install 'libpod-parser-perl' 'liburi-encode-perl' 'libwww-perl' \
    'liblwp-protocol-https-perl' 'libhttp-cookies-perl' 'libio-socket-ssl-perl' 'liburi-perl' \
    'libcryptx-perl' 'libjson-xs-perl' 'libjson-path-perl'
RUN cpanm install Net::Curl::Easy
RUN mkdir /var/lib/centreon/ \
    mkdir /var/lib/centreon/centplugins/