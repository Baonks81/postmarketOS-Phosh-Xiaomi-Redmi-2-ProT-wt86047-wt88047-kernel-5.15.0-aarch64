# postmarketOS-Phosh-Xiaomi-Redmi-2-ProT-wt86047-wt88047-kernel-5.15.0-aarch64
pmOS on xiaomi redmi 2 wt86047 wr88047

Link lk2nd, rootfs, twrp, unlock bootloader

https://drive.google.com/drive/folders/1LnHHdc0s-CVMFgR6hCuHxJg4_BUutxxT



default user is user, passwd is 147147



Thao khảo trên wiki, Redmi 2 được hỗ trợ full, community branch:

https://wiki.postmarketos.org/wiki/Xiaomi_Redmi_2_(xiaomi-wt88047)



Xiaomi MI 2/2S (xiaomi-aries) & Xiaomi Redmi 2 (wt86047/wt88047) using factory stock ROM Android 4.2/4.4 to unlock bootloader, no need mi_unlock tool



Redmi 2 variants:



Global wt88047: HM2014811, HM2014812, HM2014817, HM2014818, HM2014819, and HM2014821



China wt86047: HM2014813, HM2014512 and HM2014112



Redmi 2 ProT factory ROM:

https://mifirm.net/model/wt86047.ttt#cn-fastboot-dev



Installing Alpine Linux on Virutalbox:

[MEDIA=youtube]1_bsycXrFcI[/MEDIA]



Go to MI fastboot, press Power + Volume Down

Connect Redmi 2 ProT to PC/Laptop. Using MiFlash to come back stock Android 4.4, boot to Adnroid



Go to MI fastboot, press Power + Volume Down

Using Mi Bootloader Unlock Tool [No Auth ID Required]_BY_flash-firmware.blogspot.com.zip on gdrive to unlock bootloader



Go to MI fastboot, press Power + Volume Down

Instal TWRP on gdrive twrp-3.2.1-wt86047.img



# sudo fastboot flash recovery twrp-3.2.1-wt86047.img



Install firmware LineageOS

https://wiki.lineageos.org/devices/wt88047/install#updating-firmware

Enter TWRP, press hold Power + Volume Up + Volume Down

Go to Advance → ADB Sideload → Slide to install



On PC/Laptop, flash new firmware for Lineage OS (modem, wifi driver, bluetooth, etc.):



# sudo adb sideload wt86047-firmware_20161223.zip



Go to MI fastboot, press Power + Volume Down, to flash lk2nd-msm8916.img

https://github.com/msm8916-mainline/lk2nd#installation



# sudo fastboot flash boot lk2nd-msm8916.img



Build image from pmbootstrap on PC/Laptop:



# sudo apk add pmbootstrap python3 coreutils procps git android-tools



# pmbootstrap init



Channel []: edge



Vendor []: xiaomi



Device codename []: wt88047



Kernel []: mainline-modem



Enable this package? (y/n) [y]: y



Username []: user



User interface []: phosh ← hoặc plasma-mobile thì đổi ở đây



Extra packages []: nano



Choose default locale installation [en_US.UTF-8]: en_US.UTF-8



Device hostname (short form, e.g ‘foo’) []: wt88047-phosh



Build outdate packages during ‘pmbootstrap install’? (y/n) [y]: y



# pmbootstrap status



Trước khi build image thì chroot vào cài các package về local để tạo máy ảo, khỏi phải download và tạo khi build image



# pmbootstrap chroot



~/# apk add abuild build-base ccache git devicepkg-dev mkbootimg postmarketos-base ccache-cross-symlinks gcc-aarch64 g++-aarch64 crossdirect ncurses-dev bash bc bison elfutils-dev flex gmp-dev installkernel linux-headers openssl-dev perl sed binutils-aarch64



# pmbootstrap --details-to-stdout install



*** SET LOGIN PASSWORD FOR: 'user' ***

(rootfs_xiaomi-wt88047) % passwd user

New password: 147147

Retype new password: 147147



# pmbootstrap export



Image ở thư mục này: /home/[username]/.local/var/pmbootstrap/chroot_native/home/pmos/rootfs/xiaomi-wt88047.img



Boot ở đây: /home/[username]/.local/var/pmbootstrap/chroot_rootfs_xiaomi_wt88047/boot



Install rootfs, go to lk2nd fastboot: Power on the device. After it vibrates, hold Volume Down



On PC/Laptop, go to Redmi 2 ProT image folder



Unzip if you download image from gdrive

# sudo unxz -v xiaomi-wt88047.img.xz



# sudo fastboot flash userdata xiaomi-wt88047.img



# sudo fastboot erase system



# sudo fastboot reboot



Using sysctl.conf on gdrive



# sudo cp Downloads/sysctl.conf /etc



# sudo sysctl -p



Edit phoc.ini



# sudo apk add xorg-server



# sudo cvt 720 1280 58.6



# sudo nano /usr/share/phosh/phoc.ini



[output: DSI-1]

modeline = 74.50  720 768 840 960  1280 1283 1293 1326 -hsync +vsync

mode = 720x1280

scale = 2



Enjoy Phosh pmOS on Xiaomi Redmi 2 ProT!!!



Tham khảo: https://forum.xda-developers.com/t/wip-redmi-2-prot-wt86047-wt88047-phosh-plasma-mobile-postmarketos.4343957/



[MEDIA=youtube]H_QlNfT6G60[/MEDIA]
