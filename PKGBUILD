# Maintainer: sekret, mail=$(echo c2VrcmV0QHBvc3Rlby5zZQo= | base64 -d)
_pkgname=workstation-plugins-pack
_pkgname2=wpp
_vendor=linuxDSP
pkgname=linuxdsp-$_pkgname
pkgver=1
pkgrel=1
pkgdesc="linuxdsp workstation plugins pack (jack, lv2, linuxvst)"
arch=('i686' 'x86_64')
url="http://www.linuxdsp.co.uk/download/lv2/download_$_pkgname/index.html"
license=('custom')
groups=('linuxdsp')
depends=('gcc-libs' 'libx11')
optdepends=('jack: standalone apps')
provides=('linuxdsp-black-eq' 'linuxdsp-mbc2b' 'linuxdsp-sr2b' 'linuxdsp-500-series')
conflicts=('linuxdsp-black-eq' 'linuxdsp-mbc2b' 'linuxdsp-sr2b' 'linuxdsp-500-series')
install=linuxdsp.install
source=("http://www.linuxdsp.co.uk/download/lv2/download_$_pkgname2/$_pkgname-lv2.zip")
sha512sums=('da9c04ec03ae15632dc82c11b8309a3ead12833e0d74fb93462461491056075c07c79118f0ac7d1972681f2c4607997684ccd4d2c015b7766eb5baabb312ae1a')

if [ "$CARCH" = 'i686' ]; then
 _arch=x86
elif [ "$CARCH" = 'x86_64' ]; then
 _arch=x86-64
fi

_500seriesprepare() {
 cd "$srcdir/$_vendor/500SERIES/$_plugin/$_arch/"
 tar xf plugin_binaries.tar.gz
}
_prepare() {
 cd "$srcdir/$_vendor/$_plugin/$_arch/"
 tar xf plugin_binaries.tar.gz
}

_500series() {
 # LV2
 # mono
 cd "$srcdir/$_vendor/500SERIES/$_plugin/$_arch/plugin_binaries/LV2/$_pluginname1.lv2"
 for i in *ttl
 do
  install -Dm644 "$i" "$pkgdir/usr/lib/lv2/$_pluginname1.lv2/$i"
 done
 for i in *so
 do
  install -Dm755 "$i" "$pkgdir/usr/lib/lv2/$_pluginname1.lv2/$i"
 done
 # stereo
 cd "$srcdir/$_vendor/500SERIES/$_plugin/$_arch/plugin_binaries/LV2/$_pluginname2.lv2"
 for i in *ttl
 do
  install -Dm644 "$i" "$pkgdir/usr/lib/lv2/$_pluginname2.lv2/$i"
 done
 for i in *so
 do
  install -Dm755 "$i" "$pkgdir/usr/lib/lv2/$_pluginname2.lv2/$i"
 done

 # VST
 cd "$srcdir/$_vendor/500SERIES/$_plugin/$_arch/plugin_binaries/VST"
 # mono
 install -Dm755 "$_plugin-1.so" "$pkgdir/usr/lib/lxvst/$_plugin-1.so"
 # stereo
 install -Dm755 "$_plugin-2.so" "$pkgdir/usr/lib/lxvst/$_plugin-2.so"

 cd "$srcdir/$_vendor/500SERIES/$_plugin"
 install -Dm644 manual.pdf "$pkgdir/usr/share/doc/$_vendor-$_plugin/manual.pdf"
 install -Dm644 license.pdf "$pkgdir/usr/share/licenses/$pkgname/$_vendor-$_plugin/license.pdf"
}

_monostereo() {
 # LV2
 # mono
 cd "$srcdir/$_vendor/$_plugin/$_arch/plugin_binaries/LV2/$_pluginname1.lv2"
 for i in *ttl
 do
  install -Dm644 "$i" "$pkgdir/usr/lib/lv2/$_pluginname1.lv2/$i"
 done
 for i in *so
 do
  install -Dm755 "$i" "$pkgdir/usr/lib/lv2/$_pluginname1.lv2/$i"
 done
 # stereo
 cd "$srcdir/$_vendor/$_plugin/$_arch/plugin_binaries/LV2/$_pluginname2.lv2"
 for i in *ttl
 do
  install -Dm644 "$i" "$pkgdir/usr/lib/lv2/$_pluginname2.lv2/$i"
 done
 for i in *so
 do
  install -Dm755 "$i" "$pkgdir/usr/lib/lv2/$_pluginname2.lv2/$i"
 done

 # VST
 cd "$srcdir/$_vendor/$_plugin/$_arch/plugin_binaries/VST"
 # mono
 install -Dm755 "$_pluginname1.so" "$pkgdir/usr/lib/lxvst/$_pluginname1.so"
 # stereo
 install -Dm755 "$_pluginname2.so" "$pkgdir/usr/lib/lxvst/$_pluginname2.so"

 # JACK
 cd "$srcdir/$_vendor/$_plugin/$_arch/plugin_binaries/JACK"
 install -Dm755 "$_pluginname2-$_arch" "$pkgdir/usr/bin/$_vendor-$_pluginname2"

 cd "$srcdir/$_vendor/$_plugin"
 install -Dm644 manual.pdf "$pkgdir/usr/share/doc/$_vendor-$_plugin/manual.pdf"
 install -Dm644 license.pdf "$pkgdir/usr/share/licenses/$pkgname/$_vendor-$_plugin/license.pdf"
}

_mono() {
 # LV2
 cd "$srcdir/$_vendor/$_plugin/$_arch/plugin_binaries/LV2/$_pluginname.lv2"
 for i in *ttl
 do
  install -Dm644 "$i" "$pkgdir/usr/lib/lv2/$_pluginname.lv2/$i"
 done
 for i in *so
 do
  install -Dm755 "$i" "$pkgdir/usr/lib/lv2/$_pluginname.lv2/$i"
 done

 # VST
 cd "$srcdir/$_vendor/$_plugin/$_arch/plugin_binaries/VST"
 install -Dm755 "$_pluginname.so" "$pkgdir/usr/lib/lxvst/$_pluginname.so"

 # JACK
 cd "$srcdir/$_vendor/$_plugin/$_arch/plugin_binaries/JACK"
 install -Dm755 "$_pluginname-$_arch" "$pkgdir/usr/bin/$_vendor-$_pluginname"

 cd "$srcdir/$_vendor/$_plugin"
 install -Dm644 manual.pdf "$pkgdir/usr/share/doc/$_vendor-$_plugin/manual.pdf"
 install -Dm644 license.pdf "$pkgdir/usr/share/licenses/$pkgname/$_vendor-$_plugin/license.pdf"
}

prepare() {
 _plugin=DYN500
 _500seriesprepare
 _plugin=EQ500
 _500seriesprepare
 _plugin=GT500
 _500seriesprepare
 _plugin=BLACK-EQ
 _prepare
 _plugin=MBC2B
 _prepare
 _plugin=SR2B
 _prepare
}

package() {
 ##########
 # DYN500 #
 ##########
 _plugin=DYN500
 _pluginname1=dyn1-500
 _pluginname2=dyn2-500
 _500series


 #########
 # EQ500 #
 #########
 _plugin=EQ500
 _pluginname1=eq1-500
 _pluginname2=eq2-500
 _500series


 #########
 # GT500 #
 #########
 _plugin=GT500
 _pluginname1=gt1-500
 _pluginname2=gt2-500
 _500series


 ############
 # BLACK-EQ #
 ############
 _plugin=BLACK-EQ
 _pluginname1=black-eq1
 _pluginname2=black-eq2
 _monostereo


 #########
 # MBC2B #
 #########
 _plugin=MBC2B
 _pluginname=mbc2b
 _mono


 ########
 # SR2B #
 ########
 _plugin=SR2B
 _pluginname=sr2b
 _mono
}
