# Contributor: Snorre Jensen snojen@gmail.com
# Original submitter: sunn
#################################################################################################

# Use personalconfig of stable version (~/.openttd)? yes=.openttd / no=.openttd-beta
_org_config=yes

# set yes here for those opdepends packages you have or plan to install
# this will generate symlinks from /usr/share/openttd/data to /usr/share/opentt-beta
# Set to no if you run a dedicated server and dont have optdepends installed

_opengfx=yes
_opensfx=yes
_openmsx=no

#################################################################################################

pkgname=openttd-beta
pkgver=1.5.0_RC1
pkgrel=1
pkgdesc="Simulation game based upon Transport Tycoon Deluxe"
arch=('i686' 'x86_64')
url="http://www.openttd.org"
license=('GPL')
depends=(libpng sdl fontconfig icu)
makedepends=(lzo2)
optdepends=('openttd-opengfx: free graphics' 
            'openttd-opensfx: free soundset'
            'openttd-openmsx: free musicset')

source=(http://binaries.openttd.org/releases/${pkgver/_/-}/openttd-${pkgver/_/-}-source.tar.xz)
md5sums=('96f432d63acc882e52375c406a5ba1b6')

if [ $_org_config = yes ]; then
	_personaldir=.openttd
else
	_personaldir=.${pkgname}
fi

package() {
    cd openttd-${pkgver/_/-}
     
    ./configure \
    --prefix-dir=/usr \
    --binary-dir=bin \
    --binary-name=${pkgname} \
    --data-dir=share/${pkgname} \
    --doc-dir=share/doc/${pkgname} \
    --personal-dir=${_personaldir} \
    --install-dir=$pkgdir \
    --menu-name="OpenTTD ${pkgver/_/-}"
    make || return 1
    make install || return 1

if [ $_opengfx = yes ]; then
   mkdir $pkgdir/usr/share/${pkgname}/data
   cd $pkgdir/usr/share/${pkgname}/data
   ln -s /usr/share/openttd/data/ogfx1_base.grf .
   ln -s /usr/share/openttd/data/ogfxc_arctic.grf .
   ln -s /usr/share/openttd/data/ogfxe_extra.grf .
   ln -s /usr/share/openttd/data/ogfxh_tropical.grf .
   ln -s /usr/share/openttd/data/ogfxi_logos.grf .
   ln -s /usr/share/openttd/data/ogfxt_toyland.grf .
fi

if [ $_opensfx = yes ]; then
   ln -s /usr/share/openttd/data/opengfx.obg .
   ln -s /usr/share/openttd/data/opensfx.cat .
   ln -s /usr/share/openttd/data/opensfx.obs .
fi

if [ $_openmsx = yes ]; then
   mkdir $pkgdir/usr/share/${pkgname}/gm
   cd $pkgdir/usr/share/${pkgname}/gm
   ln -s /usr/share/openttd/gm/5432gone_redfarn.mid .
   ln -s /usr/share/openttd/gm/be_sharp_bw_redfarn.mid .
   ln -s /usr/share/openttd/gm/big_man_boogie_redfarn.mid .
   ln -s /usr/share/openttd/gm/boogi_marabi_redfarn.mid .
   ln -s /usr/share/openttd/gm/busy_schedule.mid .
   ln -s /usr/share/openttd/gm/careless_perc_redfarn.mid .
   ln -s /usr/share/openttd/gm/chemistry_lab.mid .
   ln -s /usr/share/openttd/gm/chuggachugga.mid .
   ln -s /usr/share/openttd/gm/city_blues_redfarn.mid .
   ln -s /usr/share/openttd/gm/coconut_run2.mid .
   ln -s /usr/share/openttd/gm/flying_scotsman.mid .
   ln -s /usr/share/openttd/gm/harp_harmony.mid .
   ln -s /usr/share/openttd/gm/linns_basket.mid .
   ln -s /usr/share/openttd/gm/midnight_snow_run.mid .
   ln -s /usr/share/openttd/gm/mighty_giant_run.mid .
   ln -s /usr/share/openttd/gm/modern_motion.mid .
   ln -s /usr/share/openttd/gm/moo_redfarn.mid .
   ln -s /usr/share/openttd/gm/mosey_along_redfarn.mid .
   ln -s /usr/share/openttd/gm/no_work_song_redfarn.mid .
   ln -s /usr/share/openttd/gm/openmsx.obm .
   ln -s /usr/share/openttd/gm/relax_song.mid .
   ln -s /usr/share/openttd/gm/run_for_your_life.mid .
   ln -s /usr/share/openttd/gm/say_what_redfarn.mid .
   ln -s /usr/share/openttd/gm/slow_neasy_redfarn.mid .
   ln -s /usr/share/openttd/gm/the_fast_route.mid .
   ln -s /usr/share/openttd/gm/the_hobo_redfarn.mid .
   ln -s /usr/share/openttd/gm/train_filled_with_cash.mid .
   ln -s /usr/share/openttd/gm/ttsong_iii_imuh3.mid .
   ln -s /usr/share/openttd/gm/ttsong_iv_imuh3.mid .
   ln -s /usr/share/openttd/gm/tttheme2.mid .
   ln -s /usr/share/openttd/gm/ultimate_run.mid .
   ln -s /usr/share/openttd/gm/wood_whistles.mid .
fi


}
