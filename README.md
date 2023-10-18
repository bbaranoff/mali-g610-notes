# mali-g610-notes OrangePi5Plus
Few tips for mali graphics
``bash
PRETTY_NAME="Armbian 23.8.3 jammy"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.armbian.com"
SUPPORT_URL="https://forum.armbian.com"
BUG_REPORT_URL="https://www.armbian.com/bugs"
PRIVACY_POLICY_URL="https://www.armbian.com"
UBUNTU_CODENAME=jammy
ARMBIAN_PRETTY_NAME="Armbian 23.8.3 jammy"
``
```bash
pip install -U packaging
mkdir graphics
cd graphics
git clone https://github.com/JeffyCN/rockchip_mirrors
cd ..
git clone https://github.com/rockchip-linux/kernel
cd ../rockchips_mirrors # (pick 66)
./build/env_setup.sh
make menuconfig
```
enable openssl compilation library->crypto->openssl
```bash
make -j8
cd ..
git clone https://github.com/KhronosGroup/OpenCL-SDK
cd OpenCL-SDK
git submodule init
git submodule update --recursive
mkdir build && cd build
cmake ..
make -j8
sudo make install

git clone --recurse-submodules https://github.com/KhronosGroup/Vulkan-Samples.git
git submodule init
git submodule update --recursive
mkdir build && cd build
cmake ..
make -j8
make install

git clone --recurse-submodules https://github.com/gnome/gtk.git
git submodule init
git submodule update --recursive
mkdir build && cd build
nano meson_options.txt
apt remove gdm3 gdm *gtk* *gnome* -y
apt autoremove
apt build-dep gtk4 -y

```txt
option('vulkan',
       type: 'feature',
       value: 'enabled',
       description : 'Enable support for the experimental Vulkan renderer')
```txt
./make-release.sh

git clone --recurse-submodules https://github.com/gnome/gdm.git
git submodule init
git submodule update --recursive
mkdir build && cd build
cmake ..
make -j8
sudo make install
```

