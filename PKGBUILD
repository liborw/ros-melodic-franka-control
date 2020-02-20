
# Maintainer: 
pkgname="ros-melodic-franka-control"
pkgver="0.6.0"
pkgrel=1
pkgdesc="franka_control provides a hardware node to control a Franka Emika research robot"
arch=('x86_64')
url="http://wiki.ros.org/franka_control"
license=('Apache 2.0')

makedepends=(

'ros-melodic-message-generation'
'ros-melodic-libfranka'

)

depends=(

'ros-melodic-libfranka'
'ros-melodic-franka-description'
'ros-melodic-franka-gripper'
'ros-melodic-joint-state-publisher'
'ros-melodic-message-runtime'
'ros-melodic-robot-state-publisher'

)

provides=($pkgname)
conflicts=($pkgname)
_dir="franka_ros-release-release-melodic-franka_control-0.6.0-1"
source=("$pkgname-$pkgver.tar.gz::https://github.com/frankaemika/franka_ros-release/archive/release/melodic/franka_control/0.6.0-1.tar.gz"
        "fix_pthread.patch")
md5sums=('f476f34d7351f3da95f78151fef5e0e9'
         '208ddfcf5cf985f1bbd6a9c4bb9c2352')

build() {
	# Use ROS environment variables
  	source /usr/share/ros-build-tools/clear-ros-env.sh
  	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Create build directory
  	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  	cd ${srcdir}/build

	# Build project
	cmake ${srcdir}/${_dir} \
	      -DCMAKE_BUILD_TYPE=Release \
	      -DCATKIN_BUILD_BINARY_PACKAGE=ON \
	      -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
	      -DPYTHON_EXECUTABLE=/usr/bin/python3 \
	      -DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
