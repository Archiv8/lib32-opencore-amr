#!/bin/bash

# Created from the original package by

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [Query]: Is package still being maintained.  Last release was 3.100, 2017-10-13.  Latest commit was 2021-06-19.
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: morguldir <morguldir@protonmail.com>
# Contributor: Ionut Biru <ionut@archlinux.ro>
# Contributor: WAntilles <wantilles@adslgr.com>
# Contributor: GordonGR <gordongr@freemail.gr>

_relname=opencore-amr

pkgname=lib32-opencore-amr
pkgver=0.1.5
pkgrel=4
pkgdesc="Open source implementation of the Adaptive Multi Rate (AMR) speech codec, lib32"
arch=("x86_64")
license=("APACHE")
url="http://opencore-amr.sourceforge.net/"
source=("http://downloads.sourceforge.net/sourceforge/$_relname/$_relname-$pkgver.tar.gz")
depends=(
    "$_relname"
    "glibc"
    "lib32-gcc-libs"
     )
# makedepends=(
#    )
sha512sums=(
    "c324db9dcac5a31bfac633153bc054bfe42d5ff98202c4adb3c75a3fae9792f07f60d48cd659acf106dacd307174a62b2aeee22a4af53caa20d2bfba46488faf"
    )

build() {
    export CC="gcc -m32"
    export CXX="g++ -m32"
    export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

    cd "$srcdir/$_relname-$pkgver"
    ./configure --prefix=/usr --disable-static --libdir=/usr/lib32 --libexecdir=/usr/lib32
    make
}

package() {
    cd "$srcdir/$_relname-$pkgver"
    make DESTDIR="$pkgdir" install
    cd "$pkgdir/usr"
    rm -rf include/
}

