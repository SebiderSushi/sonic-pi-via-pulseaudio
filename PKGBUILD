# Maintainer: Sebastian Zeller <SebiderSushi at t-online dot de>
pkgname=sonic-pi-via-pulseaudio
pkgver=1.0
pkgrel=1
pkgdesc="A wrapper script making sonic-pi audible through PulseAudio"
arch=('any')
url="https://github.com/SebiderSushi/sonic-pi-via-pulseaudio"
license=('Unlicense' 'MIT')
depends=('sonic-pi' 'pulseaudio-jack')
source=( "LICENSE-MIT"
         "sonic-pi-via-pulseaudio"
         "sonic-pi-via-pulseaudio.desktop")
md5sums=('f99346226fb4adcfba2b0942806ab97c'
         '74c85b74803b37946c523920790fc924'
         '376f10926e3074caf7359152ddbe04a8')

package() {
  install -Dm755 -t "$pkgdir/usr/bin/" "sonic-pi-via-pulseaudio"
  install -Dm644 -t "$pkgdir/usr/share/applications/" "sonic-pi-via-pulseaudio.desktop"
  install -Dm644 -t "$pkgdir/usr/share/licenses/$pkgname" "LICENSE-MIT"
}
