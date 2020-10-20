# ytl-linux
An easy-to-install Linux to run virtual exam server (KTP)

This is work in progress.

## Building the image

The build script will download a Ubuntu installation ISO image and modify
it so that it will boot by default to an autoinstall mode and download
our install configuration.

Just run

    ./build-ytl-image

which should result in a new ISO file "ytl-install.iso".

## Testing instructions

In its current state the image will fetch the autoinstall configuration
(located in the docs/autoinstall-config subdirectory) over the network
from GitHub. This can be changed by modifying the build script.

The image can be tested in KVM with something like this:

- make a filesystem for a "virtual hard disk"

        qemu-img create -f qcow2 test.img 8G

- run a virtual KVM machine

        kvm -hda test.img -cdrom ytl-install.iso -m 2048
