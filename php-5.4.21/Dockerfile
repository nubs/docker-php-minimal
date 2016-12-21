FROM nubs/arch-build

MAINTAINER Spencer Rinehart <anubis@overthemonkey.com>

COPY php/PKGBUILD php/*.patch /package/

RUN makepkg --force

USER root

RUN pacman --upgrade --noconfirm --noprogressbar php-*-x86_64.pkg.tar.xz

COPY php.ini /etc/php/php.ini

USER build

CMD ["php"]
