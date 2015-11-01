FROM mparker17/drupal7

# Setup the Xdebug version to install.
ENV XDEBUG_VERSION 2.3.3
ENV XDEBUG_MD5 60e6fdf41840104a23debe16db15a2af

# Install Xdebug.
RUN set -x && \
    curl -SL "http://www.xdebug.org/files/xdebug-$XDEBUG_VERSION.tgz" -o xdebug.tgz && \
    echo $XDEBUG_MD5 xdebug.tgz | md5sum -c - && \
    mkdir -p /usr/src/xdebug && \
    tar -xf xdebug.tgz -C /usr/src/xdebug --strip-components=1 && \
    rm xdebug.* && \
    cd /usr/src/xdebug && \
    phpize && \
    ./configure && \
    make -j"$(nproc)" && \
    make install && \
    make clean

ADD ext-xdebug.ini /usr/local/etc/php/conf.d/
