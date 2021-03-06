# my_linux_conf

# What is Repo  

Repo is a tool built on top of Git. Repo helps manage many Git repositories, does the uploads to revision control systems, and automates parts of the development workflow. Repo is not meant to replace Git, only to make it easier to work with Git. The repo command is an executable Python script that you can put anywhere in your path.

> More info, Please refer the official doc `repo`:https://github.com/aosp-mirror/tools_repo

# About Repo And Manifest XML File

```sh
$ repo init -u url
```

Installs Repo in the current directory. This creates a .repo/ directory with Git repositories for the Repo source code and the standard Android manifest files.

Options:

+ **-u** : Specify a URL from which to retrieve a manifest repository. The common manifest is found at https://android.googlesource.com/platform/manifest
+ **-m** : Select a manifest file within the repository. If no manifest name is selected, the default is default.xml.
+ **-b** : Specify a revision, that is, a particular manifest-branch.

**eg. A standard manifest file (default.xml) is as follows:**

```xml

<?xml version="1.0" encoding="UTF-8"?>
<manifest>

  <remote  name="origin"
           fetch="https://github.com/ABigBright/" />
  
  <remote  name="origin1"
           fetch="https://github.com/ABigBright/" />

  <default revision="refs/heads/master"
           remote="origin"
           sync-j="4" />

  <project path=".config/alacritty" name="alacritty_conf" remote="origin" revision="refs/heads/master"/>
  <project path=".config/albert" name="albert_conf" remote="origin" revision="refs/heads/master"/>
  <project path=".config/ranger" name="ranger_conf" remote="origin" revision="refs/heads/master"/>



  <!-- <project path="build" name="android_build" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" > -->
  <!--   <copyfile src="core/root.mk" dest="Makefile" /> -->
  <!-- </project> -->
  <!-- <project path="abi/cpp" name="platform/abi/cpp" /> -->
  <!-- <project path="bionic" name="android_bionic" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="bootable/bootloader/legacy" name="platform/bootable/bootloader/legacy" /> -->
  <!-- <project path="bootable/diskinstaller" name="platform/bootable/diskinstaller" /> -->
  <!-- <project path="bootable/recovery" name="android_bootable_recovery"  remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="cts" name="platform/cts" /> -->
  <!-- <project path="dalvik" name="platform/dalvik" /> -->
  <!-- <project path="development" name="android_development" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="device/common" name="device/common" /> -->
  <!-- <project path="device/generic/goldfish" name="device/generic/goldfish" /> -->
  <!-- <project path="device/google/accessory/arduino" name="device/google/accessory/arduino" /> -->
  <!-- <project path="device/google/accessory/demokit" name="device/google/accessory/demokit" /> -->
  <!-- <project path="device/moto/common" name="device/moto/common" /> -->
  <!-- <project path="device/moto/stingray" name="device/moto/stingray" /> -->
  <!-- <project path="device/moto/wingray" name="device/moto/wingray" /> -->
  <!-- <project path="device/sample" name="device/sample" /> -->
  <!-- <project path="device/samsung/smdk4x12" name="android_device_samsung_smdk4x12" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" > -->
  <!--    <copyfile src="build_android.sh" dest="build_android.sh" /> -->
  <!--    <copyfile src="make_system_only.sh" dest="make_system_only.sh" /> -->
  <!-- </project> -->
  <!-- <project path="device/samsung/exynos4" name="android_device_samsung_exynos4" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="device/samsung/common" name="android_device_samsung_common" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="device/samsung/smdk_common" name="android_device_samsung_smdk_common" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="device/samsung/multimedia" name="android_device_samsung_multimedia" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"  /> -->
  <!-- <project path="docs/source.android.com" name="android_docs_source.android.com" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"  /> -->
  <!-- <project path="external/android-mock" name="platform/external/android-mock" /> -->
  <!-- <project path="external/antlr" name="platform/external/antlr" /> -->
  <!-- <project path="external/apache-harmony" name="platform/external/apache-harmony" /> -->
  <!-- <project path="external/apache-http" name="platform/external/apache-http" /> -->
  <!-- <project path="external/apache-xml" name="platform/external/apache-xml" /> -->
  <!-- <project path="external/astl" name="platform/external/astl" /> -->
  <!-- <project path="external/bison" name="platform/external/bison" /> -->
  <!-- <project path="external/blktrace" name="platform/external/blktrace" /> -->
  <!-- <project path="external/bluetooth/bluez" name="android_external_bluetooth_bluez" remote="origin"  revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="external/bluetooth/glib" name="platform/external/bluetooth/glib" /> -->
  <!-- <project path="external/bluetooth/hcidump" name="platform/external/bluetooth/hcidump" /> -->
  <!-- <project path="external/bouncycastle" name="platform/external/bouncycastle" /> -->
  <!-- <project path="external/bsdiff" name="platform/external/bsdiff" /> -->
  <!-- <project path="external/bzip2" name="platform/external/bzip2" /> -->
  <!-- <project path="external/chromium" name="platform/external/chromium" /> -->
  <!-- <project path="external/clang" name="platform/external/clang" /> -->
  <!-- <project path="external/collada" name="platform/external/collada" /> -->
  <!-- <project path="external/dbus" name="platform/external/dbus" /> -->
  <!-- <project path="external/dhcpcd" name="android_external_dhcpcd" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/dnsmasq" name="platform/external/dnsmasq" /> -->
  <!-- <project path="external/doclava" name="platform/external/doclava" /> -->
  <!-- <project path="external/dropbear" name="platform/external/dropbear" /> -->
  <!-- <project path="external/e2fsprogs" name="platform/external/e2fsprogs" /> -->
  <!-- <project path="external/easymock" name="platform/external/easymock" /> -->
  <!-- <project path="external/elfutils" name="platform/external/elfutils" /> -->
  <!-- <project path="external/embunit" name="platform/external/embunit" /> -->
  <!-- <project path="external/emma" name="platform/external/emma" /> -->
  <!-- <project path="external/esd" name="platform/external/esd" /> -->
  <!-- <project path="external/expat" name="platform/external/expat" /> -->
  <!-- <project path="external/eyes-free" name="platform/external/eyes-free" /> -->
  <!-- <project path="external/fdlibm" name="platform/external/fdlibm" /> -->
  <!-- <project path="external/flac" name="platform/external/flac" /> -->
  <!-- <project path="external/freetype" name="platform/external/freetype" /> -->
  <!-- <project path="external/fsck_msdos" name="platform/external/fsck_msdos" /> -->
  <!-- <project path="external/genext2fs" name="platform/external/genext2fs" /> -->
  <!-- <project path="external/giflib" name="platform/external/giflib" /> -->
  <!-- <project path="external/google-diff-match-patch" name="platform/external/google-diff-match-patch" /> -->
  <!-- <project path="external/grub" name="platform/external/grub" /> -->
  <!-- <project path="external/gtest" name="platform/external/gtest" /> -->
  <!-- <project path="external/guava" name="platform/external/guava" /> -->
  <!-- <project path="external/harfbuzz" name="platform/external/harfbuzz" /> -->
  <!-- <project path="external/hyphenation" name="platform/external/hyphenation" /> -->
  <!-- <project path="external/icu4c" name="platform/external/icu4c" /> -->
  <!-- <project path="external/iproute2" name="platform/external/iproute2" /> -->
  <!-- <project path="external/ipsec-tools" name="platform/external/ipsec-tools" /> -->
  <!-- <project path="external/iptables" name="platform/external/iptables" /> -->
  <!-- <project path="external/javasqlite" name="platform/external/javasqlite" /> -->
  <!-- <project path="external/javassist" name="platform/external/javassist" /> -->
  <!-- <project path="external/jdiff" name="platform/external/jdiff" /> -->
  <!-- <project path="external/jhead" name="platform/external/jhead" /> -->
  <!-- <project path="external/jpeg" name="platform/external/jpeg" /> -->
  <!-- <project path="external/jsilver" name="platform/external/jsilver" /> -->
  <!-- <project path="external/jsr305" name="platform/external/jsr305" /> -->
  <!-- <project path="external/junit" name="platform/external/junit" /> -->
  <!-- <project path="external/kernel-headers" name="platform/external/kernel-headers" /> -->
  <!-- <project path="external/libffi" name="platform/external/libffi" /> -->
  <!-- <project path="external/libgsm" name="platform/external/libgsm" /> -->
  <!-- <project path="external/liblzf" name="platform/external/liblzf" /> -->
  <!-- <project path="external/libnfc-nxp" name="android_external_libnfc-nxp" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="external/libnl-headers" name="platform/external/libnl-headers" /> -->
  <!-- <project path="external/libpcap" name="platform/external/libpcap" /> -->
  <!-- <project path="external/libphonenumber" name="platform/external/libphonenumber" /> -->
  <!-- <project path="external/libpng" name="platform/external/libpng" /> -->
  <!-- <project path="external/libvpx" name="platform/external/libvpx" /> -->
  <!-- <project path="external/libxml2" name="platform/external/libxml2" /> -->
  <!-- <project path="external/libxslt" name="platform/external/libxslt" /> -->
  <!-- <project path="external/libyuv" name="platform/external/libyuv" /> -->
  <!-- <project path="external/llvm" name="platform/external/llvm" /> -->
  <!-- <project path="external/lohit-fonts" name="platform/external/lohit-fonts" /> -->
  <!-- <project path="external/markdown" name="platform/external/markdown" /> -->
  <!-- <project path="external/mesa3d" name="platform/external/mesa3d" /> -->
  <!-- <project path="external/mksh" name="platform/external/mksh" /> -->
  <!-- <project path="external/mockwebserver" name="platform/external/mockwebserver" /> -->
  <!-- <project path="external/mtpd" name="platform/external/mtpd" /> -->
  <!-- <project path="external/netcat" name="platform/external/netcat" /> -->
  <!-- <project path="external/netperf" name="platform/external/netperf" /> -->
  <!-- <project path="external/neven" name="platform/external/neven" /> -->
  <!-- <project path="external/nist-sip" name="platform/external/nist-sip" /> -->
  <!-- <project path="external/oauth" name="platform/external/oauth" /> -->
  <!-- <project path="external/opencv" name="platform/external/opencv" /> -->
  <!-- <project path="external/openssl" name="platform/external/openssl" /> -->
  <!-- <project path="external/oprofile" name="platform/external/oprofile" /> -->
  <!-- <project path="external/pcre" name="platform/external/pcre" /> -->
  <!-- <project path="external/ping" name="platform/external/ping" /> -->
  <!-- <project path="external/ping6" name="platform/external/ping6" /> -->
  <!-- <project path="external/ppp" name="platform/external/ppp" /> -->
  <!-- <project path="external/proguard" name="platform/external/proguard" /> -->
  <!-- <project path="external/protobuf" name="platform/external/protobuf" /> -->
  <!-- <project path="external/qemu" name="platform/external/qemu" /> -->
  <!-- <project path="external/qemu-pc-bios" name="platform/external/qemu-pc-bios" /> -->
  <!-- <project path="external/quake" name="platform/external/quake" /> -->
  <!-- <project path="external/safe-iop" name="platform/external/safe-iop" /> -->
  <!-- <project path="external/skia" name="android_external_skia" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/sonivox" name="platform/external/sonivox" /> -->
  <!-- <project path="external/speex" name="platform/external/speex" /> -->
  <!-- <project path="external/sqlite" name="platform/external/sqlite" /> -->
  <!-- <project path="external/srec" name="platform/external/srec" /> -->
  <!-- <project path="external/srtp" name="platform/external/srtp" /> -->
  <!-- <project path="external/stlport" name="platform/external/stlport" /> -->
  <!-- <project path="external/strace" name="platform/external/strace" /> -->
  <!-- <project path="external/svox" name="platform/external/svox" /> -->
  <!-- <project path="external/tagsoup" name="platform/external/tagsoup" /> -->
  <!-- <project path="external/tcpdump" name="platform/external/tcpdump" /> -->
  <!-- <project path="external/tinyalsa" name="platform/external/tinyalsa" /> -->
  <!-- <project path="external/tinyxml" name="platform/external/tinyxml" /> -->
  <!-- <project path="external/tremolo" name="platform/external/tremolo" /> -->
  <!-- <project path="external/v8" name="platform/external/v8" /> -->
  <!-- <project path="external/valgrind" name="platform/external/valgrind" /> -->
  <!-- <project path="external/webkit" name="platform/external/webkit" /> -->
  <!-- <project path="external/webp" name="platform/external/webp" /> -->
  <!-- <project path="external/webrtc" name="platform/external/webrtc" /> -->
  <!-- <project path="external/wpa_supplicant" name="platform/external/wpa_supplicant" /> -->
  <!-- <project path="external/wpa_supplicant_6" name="android_external_wpa_supplicant_6" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/wpa_supplicant_8" name="android_external_wpa_supplicant_8" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/xmlwriter" name="platform/external/xmlwriter" /> -->
  <!-- <project path="external/yaffs2" name="platform/external/yaffs2" /> -->
  <!-- <project path="external/zlib" name="platform/external/zlib" /> -->
  <!-- <project path="external/semco" name="android_external_semco" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="external/ath6kl-fwlog" name="android_external_ath6kl-fwlog" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/ath6kl_fw" name="android_external_ath6kl_fw" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/tslib" name="android_external_tslib" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/wlan_tool" name="android_external_wlan_tool" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/hostap-ccx" name="android_external_hostap-ccx" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/iperf-2.0.4" name="android_external_iperf-2.0.4" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/wireless_tools_29" name="android_external_wireless_tools_29" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="external/libsnfc-fw" name="android_external_libsnfc-fw" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!--  -->
  <!--  -->
  <!-- <project path="frameworks/base" name="android_frameworks_base" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="frameworks/compile/libbcc" name="platform/frameworks/compile/libbcc" /> -->
  <!-- <project path="frameworks/compile/linkloader" name="platform/frameworks/compile/linkloader" /> -->
  <!-- <project path="frameworks/compile/slang" name="platform/frameworks/compile/slang" /> -->
  <!-- <project path="frameworks/ex" name="platform/frameworks/ex" /> -->
  <!-- <project path="frameworks/media/libvideoeditor" name="android_frameworks_media_libvideoeditor" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="frameworks/opt/calendar" name="platform/frameworks/opt/calendar" /> -->
  <!-- <project path="frameworks/opt/emoji" name="platform/frameworks/opt/emoji" /> -->
  <!-- <project path="frameworks/opt/inputmethodcommon" name="platform/frameworks/opt/inputmethodcommon" /> -->
  <!-- <project path="frameworks/opt/mailcommon" name="platform/frameworks/opt/mailcommon" /> -->
  <!-- <project path="frameworks/opt/vcard" name="platform/frameworks/opt/vcard" /> -->
  <!-- <project path="frameworks/support" name="platform/frameworks/support" /> -->
  <!--  -->
  <!-- <project path="hardware/broadcom/wlan" name="platform/hardware/broadcom/wlan" /> -->
  <!-- <project path="hardware/gps" name="android_hardware_gps" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" 	/> -->
  <!-- <project path="hardware/libhardware" name="android_hardware_libhardware"  remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="hardware/libhardware_legacy" name="android_hardware_libhardware_legacy" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="hardware/msm7k" name="platform/hardware/msm7k" /> -->
  <!-- <project path="hardware/qcom/gps" name="platform/hardware/qcom/gps" /> -->
  <!-- <project path="hardware/qcom/media" name="platform/hardware/qcom/media" /> -->
  <!-- <project path="hardware/ril" name="android_hardware_ril" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="hardware/ti/omap3" name="platform/hardware/ti/omap3" /> -->
  <!-- <project path="hardware/ti/omap4xxx" name="platform/hardware/ti/omap4xxx" /> -->
  <!--  -->
  <!-- <project path="libcore" name="platform/libcore" /> -->
  <!-- <project path="ndk" name="platform/ndk" /> -->
  <!-- <project path="packages/apps/BasicSmsReceiver" name="platform/packages/apps/BasicSmsReceiver" /> -->
  <!-- <project path="packages/apps/Bluetooth" name="platform/packages/apps/Bluetooth" /> -->
  <!-- <project path="packages/apps/Browser" name="android_packages_apps_Browser" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="packages/apps/Calculator" name="platform/packages/apps/Calculator" /> -->
  <!-- <project path="packages/apps/Calendar" name="platform/packages/apps/Calendar" /> -->
  <!-- <project path="packages/apps/Camera" name="android_packages_apps_Camera" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="packages/apps/SEC_Camera" name="android_packages_apps_SEC_Camera" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="packages/apps/CellBroadcastReceiver" name="platform/packages/apps/CellBroadcastReceiver" /> -->
  <!-- <project path="packages/apps/CertInstaller" name="platform/packages/apps/CertInstaller" /> -->
  <!-- <project path="packages/apps/Contacts" name="platform/packages/apps/Contacts" /> -->
  <!-- <project path="packages/apps/DeskClock" name="platform/packages/apps/DeskClock" /> -->
  <!-- <project path="packages/apps/Email" name="platform/packages/apps/Email" /> -->
  <!-- <project path="packages/apps/Exchange" name="platform/packages/apps/Exchange" /> -->
  <!-- <project path="packages/apps/Gallery" name="platform/packages/apps/Gallery" /> -->
  <!-- <project path="packages/apps/Gallery2" name="android_packages_apps_Gallery2"  remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="packages/apps/HTMLViewer" name="platform/packages/apps/HTMLViewer" /> -->
  <!-- <project path="packages/apps/KeyChain" name="platform/packages/apps/KeyChain" /> -->
  <!-- <project path="packages/apps/Launcher2" name="platform/packages/apps/Launcher2" /> -->
  <!-- <project path="packages/apps/Mms" name="platform/packages/apps/Mms" /> -->
  <!-- <project path="packages/apps/Music" name="platform/packages/apps/Music" /> -->
  <!-- <project path="packages/apps/MusicFX" name="platform/packages/apps/MusicFX" /> -->
  <!-- <project path="packages/apps/MusicULP" name="android_packages_apps_MusicULP"  remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="packages/apps/Nfc" name="android_packages_apps_Nfc" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="packages/apps/PackageInstaller" name="platform/packages/apps/PackageInstaller" /> -->
  <!-- <project path="packages/apps/Phone" name="platform/packages/apps/Phone" /> -->
  <!-- <project path="packages/apps/Protips" name="platform/packages/apps/Protips" /> -->
  <!-- <project path="packages/apps/Provision" name="platform/packages/apps/Provision" /> -->
  <!-- <project path="packages/apps/QuickSearchBox" name="android_packages_apps_QuickSearchBox" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="packages/apps/Settings" name="android_packages_apps_Settings"  remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="packages/apps/SoundRecorder" name="android_packages_apps_SoundRecorder" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="packages/apps/SpareParts" name="platform/packages/apps/SpareParts" /> -->
  <!-- <project path="packages/apps/SpeechRecorder" name="platform/packages/apps/SpeechRecorder" /> -->
  <!-- <project path="packages/apps/Stk" name="platform/packages/apps/Stk" /> -->
  <!-- <project path="packages/apps/Tag" name="platform/packages/apps/Tag" /> -->
  <!-- <project path="packages/apps/VideoEditor" name="platform/packages/apps/VideoEditor" /> -->
  <!-- <project path="packages/apps/VoiceDialer" name="platform/packages/apps/VoiceDialer" /> -->
  <!-- <project path="packages/experimental" name="platform/packages/experimental" /> -->
  <!-- <project path="packages/inputmethods/LatinIME" name="platform/packages/inputmethods/LatinIME" /> -->
  <!-- <project path="packages/inputmethods/OpenWnn" name="platform/packages/inputmethods/OpenWnn" /> -->
  <!-- <project path="packages/inputmethods/PinyinIME" name="platform/packages/inputmethods/PinyinIME" /> -->
  <!-- <project path="packages/providers/ApplicationsProvider" name="platform/packages/providers/ApplicationsProvider" /> -->
  <!-- <project path="packages/providers/CalendarProvider" name="platform/packages/providers/CalendarProvider" /> -->
  <!-- <project path="packages/providers/ContactsProvider" name="platform/packages/providers/ContactsProvider" /> -->
  <!-- <project path="packages/providers/DownloadProvider" name="platform/packages/providers/DownloadProvider" /> -->
  <!-- <project path="packages/providers/DrmProvider" name="platform/packages/providers/DrmProvider" /> -->
  <!-- <project path="packages/providers/GoogleContactsProvider" name="platform/packages/providers/GoogleContactsProvider" /> -->
  <!-- <project path="packages/providers/MediaProvider" name="platform/packages/providers/MediaProvider" /> -->
  <!-- <project path="packages/providers/TelephonyProvider" name="platform/packages/providers/TelephonyProvider" /> -->
  <!-- <project path="packages/providers/UserDictionaryProvider" name="platform/packages/providers/UserDictionaryProvider" /> -->
  <!-- <project path="packages/wallpapers/Basic" name="platform/packages/wallpapers/Basic" /> -->
  <!-- <project path="packages/wallpapers/Galaxy4" name="platform/packages/wallpapers/Galaxy4" /> -->
  <!-- <project path="packages/wallpapers/HoloSpiral" name="platform/packages/wallpapers/HoloSpiral" /> -->
  <!-- <project path="packages/wallpapers/LivePicker" name="platform/packages/wallpapers/LivePicker" /> -->
  <!-- <project path="packages/wallpapers/MagicSmoke" name="platform/packages/wallpapers/MagicSmoke" /> -->
  <!-- <project path="packages/wallpapers/MusicVisualization" name="platform/packages/wallpapers/MusicVisualization" /> -->
  <!-- <project path="packages/wallpapers/NoiseField" name="platform/packages/wallpapers/NoiseField" /> -->
  <!-- <project path="packages/wallpapers/PhaseBeam" name="platform/packages/wallpapers/PhaseBeam" /> -->
  <!--  -->
  <!-- <project path="prebuilt" name="platform/prebuilt" /> -->
  <!-- <project path="sdk" name="platform/sdk" /> -->
  <!-- <project path="system/bluetooth" name="android_system_bluetooth" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->
  <!-- <project path="system/core" name="android_system_core" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="system/extras" name="platform/system/extras" /> -->
  <!-- <project path="system/media" name="android_system_media" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="system/netd" name="android_system_netd" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master"/> -->
  <!-- <project path="system/vold" name="android_system_vold" remote="origin" revision="refs/heads/exynos4412_android4.0.3_master" /> -->

</manifest>

```

+ **remote** : used to specify the remote repositorys, this tag can be at least one remote repository, for exmaple there is two remote repository, one is origin, another is origin1
    + **name** : is the repository alias
    + **fetch** : is the remote repository url
+ **default** : used to configure the default option
    + **revision** : default branch
    + **remote** : default remote repository
    + **sync-j** : default parallel download task
+ **project** : used to specify the local repository 
    + **path** : local directory to be create
    + **name** : is the remote repository name, eg: name = "xxy", so when repo sync will evaluate this form : **git clone https://github.com/ABigBright/xxy**
    + **remote** : specify the remote repository
    + **revision** : specify the branch to use

**eg : the project is as follows**

```xml
  <remote  name="origin"
           fetch="https://github.com/ABigBright/" />

  <project path=".config/alacritty" name="alacritty_conf" remote="origin" revision="refs/heads/master"/>
```

# Getting Started

1. curl -fLo repo --create-dirs -H "Accept: application/vnd.github.v3.raw"  https://api.github.com/repos/ABigBright/tools_repo/contents/repo
2. export REPO_URL='https://github.com/ABigBright/tools_repo'
3. repo init -u https://github.com/ABigBright/my_linux_conf
4. repo sync
5. repo start master --all
6. check all the repository whether is right!!!

# What do these cmd do

**repo init -u https://github.com/ABigBright/my_linux_conf will do the following things:**

1. mkdir .repo directory
2. git clone google `repo` repository into .repo/repo
> we use the https://mirrors.tuna.tsinghua.edu.cn/git/git-repo for google `repo` mirror to speed up the git clone 
3. git clone https://github.com/ABigBright/my_linux_conf .repo/manifests 
> store the .git misc meta date into .repo/manifests.git


**repo sync will do the following things:**

1. mkdir the .config/alacritty directory in pwd
2. git clone https://github.com/ABigBright/alacritty_conf .config/alacritty -b master

This is a repo python script to manage multiple git repository example for learning the repo mechnism
