.. _bootable-usb-linux:

Create a bootable USB drive on Linux
************************************

Follow these instructions to create a bootable |CLOSIA| USB drive.
Use an **8GB** or larger USB drive.

Alternative instructions for other operating systems are available:

* :ref:`bootable-usb-mac`
* :ref:`bootable-usb-windows`

.. _download-cl-image:

.. include:: ../../guides/maintenance/download-image.rst
   :Start-after: types-of-cl-images:
   :end-before: verify-image-checksum

.. _download-usb-suitable-images:

Download the latest Clear Linux image
=====================================

There are 2 types of |CL| images that are suitable for burning onto and running 
off a USB drive:

   * Live image: **clear-<version number>-live.img.xz**
   * Installer image: **clear-<version number>-installer.img.xz**

Go to the Clear Linux `image`_ repository and download the desired type.

.. _image: https://download.clearlinux.org/image

.. include ../../guides/maintenance/download-image.rst
..   :Start-after: download-usb-suitable-images:
..   :end-before: verify-image-checksum

.. Download the latest Clear Linux image
.. =====================================

.. There are 2 types of |CL| images that are suitable for burning onto and running 
.. off a USB drive:

..   * Live image: `clear-<version number>-live.img.xz`
..   * Installer image: `clear-<version number>-installer.img.xz`

.. Go to the Clear Linux `image`_ repository and download the desired type.

..   * Live image: `clear-<version>-live.img.xz`
..   * Installer image: `clear-<version>-installer.img.xz`

..   For older versions, see the `releases`_ page.

.. Although not required, it is recommended to download the corresponding
..   checksum file (designated with `-SHA512SUMS` at the end of the filename) for
..   the image in order to verify its integrity.

.. verify-checksum

.. _end-download-usb-suitable-images:

.. include:: ../../guides/maintenance/download-image.rst
   :Start-after: verify-image-checksum:
   :end-before: verify-image-checksum-on-macos

.. include:: ../../guides/maintenance/download-image.rst
   :Start-after: uncompress-image:
   :end-before: uncompress-gz-on-linux

.. Verify the integrity of the download (recommended)
.. ==================================================

.. #. Start a terminal emulator.
.. #. Go to the directory with the downloaded files.
.. #. To verify the integrity of the image, enter the following (a live image
..   is used as example):

.. code-block console

..      $ sha512sum ./clear-<version>-live.img.xz | diff ./clear-<version>-live.img.xz-SHA512SUMS -

..   If the checksum of the downloaded image is different than the original
..   checksum, the differences will displayed. An empty output indicates a match.

.. _copy-usb-linux:

Burn the Clear Linux image onto a USB drive
===========================================

.. _caution-burn-usb-drive:

**Caution:** Backup important data before proceeding. The process of burning 
an image onto the USB drive completely formats the USB drive and any existing 
content will be destroyed.

.. _end-caution-burn-usb-drive:

#. Open a terminal emulator and get root privilege.

   .. code-block:: console

      $ sudo -s

#. Go to the directory with the uncompressed image.
#. Plug in the USB drive.
#. Identify the USB drive using the `lsblk` command.  This shows all drives
   attached to the system, including the primary hard disk. In the example
   output below, there are 4 drives (`/dev/sda`, `/dev/sdb`, `/dev/sdc`, and
   `/dev/sdd`) attached, where `/dev/sda` is primary drive in this case. The
   remaining are 3 USB drives. The output also shows the mounted partitions
   (under the `MOUNTPOINT` column) for each drive.

   .. code-block:: console

      # lsblk

   Example output:

   .. code-block:: console

      NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
      sdd      8:48   1    15G  0 disk
      ├─sdd2   8:50   1     5G  0 part /run/media/user1/960c184f-3bb7-42b7-bcaf-0c1282
      ├─sdd3   8:51   1     8G  0 part /run/media/user1/704f3382-b26d-4f34-af1b-cb9aab
      └─sdd1   8:49   1     2G  0 part
      sdb      8:16   1  14.8G  0 disk
      └─sdb1   8:17   1  14.8G  0 part /run/media/user1/PATRIOT_USB
      sdc      8:32   1   7.3G  0 disk
      └─sdc1   8:33   1   7.3G  0 part /run/media/user1/LINUX MINT
      sda      8:0    0 335.4G  0 disk
      ├─sda4   8:4    0    28G  0 part
      ├─sda2   8:2    0   3.7G  0 part [SWAP]
      ├─sda7   8:7    0     6G  0 part /home
      ├─sda5   8:5    0     1G  0 part /boot
      ├─sda3   8:3    0   954M  0 part /boot/efi
      ├─sda1   8:1    0    28G  0 part
      ├─sda8   8:8    0    30G  0 part /
      └─sda6   8:6    0   7.9G  0 part [SWAP]

#. Before an image can be burned onto a USB drive, it should be un-mounted.
   Some Linux distros may automatically mount a USB drive when it is plugged
   in. To unmount, use the `umount` command followed by the device
   identifier/partition. For example: From the above `lsblk` output,
   `/dev/sdd` has 2 mounted partitions.  To unmount them, enter:

   .. code-block:: console

      # umount /dev/sdd2
      # umount /dev/sdd3

#. Burn the image onto the USB drive.  The command-line example below burns an 
   uncompressed image onto `/dev/sdd`: 

   .. code-block:: console

      # dd if=./clear-<version number>-<image type> of=/dev/sdd bs=4M status=progress

.. _usb-next:

Next steps
----------

With a bootable |CL| USB drive, you can:

* :ref:`bare-metal-install`
* :ref:`boot-live-image`
* :ref:`multi-boot`

.. _image: https://download.clearlinux.org/image
.. _releases: https://download.clearlinux.org/releases


