# Maintainer: irgaly <irgaly@gmail.com>
pkgname=ddclient-valuedomain
pkgver=3.8.1
pkgrel=4
pkgdesc="Update dynamic DNS entries for accounts on many dynamic DNS services.Supporting VALUE-DOMAIN."
arch=('any')
url="http://ddclient.sourceforge.net/"
license=('GPL2')
depends=('perl' 'perl-io-socket-ssl')
provides=('ddclient')
conflicts=('ddclient')
backup=('etc/ddclient/ddclient.conf' 'etc/conf.d/ddclient')
install=ddclient.install
source=("http://downloads.sourceforge.net/project/ddclient/ddclient/ddclient-$pkgver/ddclient-$pkgver.tar.bz2"
        "ddclient-valuedomain-$pkgver.patch"
        "ddclient.conf.d"
        "ddclient.service")

build() {
  cd "$srcdir/ddclient-$pkgver"

  patch < $srcdir/ddclient-valuedomain-$pkgver.patch
}

package() {
  cd "$srcdir/ddclient-$pkgver"

  # core files
  install -Dm755 {,$pkgdir/usr/bin/}ddclient
  install -Dm600 sample-etc_ddclient.conf $pkgdir/etc/ddclient/ddclient.conf
  install -Dm644 $srcdir/ddclient.conf.d $pkgdir/etc/conf.d/ddclient
  install -Dm644 {$srcdir/,$pkgdir/usr/lib/systemd/system/}ddclient.service
  install -d ${pkgdir}/var/cache/ddclient

  # additional instructions, sample configs
  install -Dm644 {,$pkgdir/etc/ddclient/samples/}README
  install -Dm644 {,$pkgdir/etc/ddclient/samples/}sample-etc_cron.d_ddclient
  install -Dm644 {,$pkgdir/etc/ddclient/samples/}sample-etc_dhcpc_dhcpcd-eth0.exe
  install -Dm644 {,$pkgdir/etc/ddclient/samples/}sample-etc_ppp_ip-up.local
}
md5sums=('7fa417bc65f8f0e6ce78418a4f631988'
         '929fdff52c924a802829107b48416055'
         'b8f39c82827776da948b76ef83544d33'
         'fc3a381ae47d8a1d56c6f0ddd8452754')
