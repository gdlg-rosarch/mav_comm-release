# Script generated with Bloom
pkgdesc="ROS - Contains messages and services for MAV communication"
url='https://github.com/ethz-asl/mav_comm'

pkgname='ros-kinetic-mav-comm'
pkgver='3.2.0_2'
pkgrel=1
arch=('any')
license=('ASL 2.0'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-mav-msgs'
)

conflicts=()
replaces=()

_dir=mav_comm
source=()
md5sums=()

prepare() {
    cp -R $startdir/mav_comm $srcdir/mav_comm
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

