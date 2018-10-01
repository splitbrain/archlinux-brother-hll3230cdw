# Maintainer: Daniel Wyatt <Daniel.Wyatt at gmail dot com>
pkgname=brother-hll3230cdw
pkgver=1.0.2
pkgrel=1
pkgdesc='Brother HL-L3230CDW CUPS driver'
arch=('i686' 'x86_64')
url='http://www.brother.com'
license=('GPL')
depends=('cups' 'perl' 'ghostscript')
source=(
  'http://download.brother.com/welcome/dlf103944/hll3230cdwpdrv-1.0.2-0.i386.rpm'
)
sha256sums=(
  '7dfbc1d2f3543e97ab7ad56b961e47df98c18347b76962408cc9b30b4e452e90'
)

package() {
  # using /usr/share instead of /opt
  mkdir -p "$pkgdir/usr/share"
  cp -R "$srcdir/opt/brother" "$pkgdir/usr/share"
  sed -i 's|\\\/opt\\\/|\\\/usr\\\/|' "$pkgdir/usr/share/brother/Printers/hll3230cdw/cupswrapper/brother_lpdwrapper_hll3230cdw"
  sed -i 's|\\\/opt\\\/|\\\/usr\\\/|' "$pkgdir/usr/share/brother/Printers/hll3230cdw/lpd/filter_hll3230cdw"

  # symlink for lpdwrapper so it correctly figures out the printer model from the path
  install -d "$pkgdir/usr/lib/cups/filter/"
  ln -s "/usr/share/brother/Printers/hll3230cdw/cupswrapper/brother_lpdwrapper_hll3230cdw" "$pkgdir/usr/lib/cups/filter/brother_lpdwrapper_hll3230cdw"

  # symlink for the PPD
  install -d "$pkgdir/usr/share/cups/model/"
  ln -s "/usr/share/brother/Printers/hll3230cdw/cupswrapper/brother_hll3230cdw_printer_en.ppd" "$pkgdir/usr/share/cups/model/"

  # symlink for inf because it tries to execute it there
  ln -s "/usr/share/brother/Printers/hll3230cdw/inf" "$pkgdir/usr/share/brother/Printers/hll3230cdw/lpd/"
}

