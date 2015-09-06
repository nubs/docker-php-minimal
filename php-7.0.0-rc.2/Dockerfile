FROM base/archlinux

MAINTAINER Spencer Rinehart <anubis@overthemonkey.com>

COPY php/php-7.0.0RC2-1-x86_64.pkg.tar.xz /tmp/php-7.0.0RC2-1-x86_64.pkg.tar.xz

RUN pacman --upgrade --noconfirm --noprogressbar /tmp/php-7.0.0RC2-1-x86_64.pkg.tar.xz

ADD php.ini /etc/php/php.ini

CMD ["php"]
