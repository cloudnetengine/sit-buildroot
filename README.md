# CNE-OVS-SIT VM image builder

## Summary

The project is used to build CNE-OVS-SIT VM image.

CNE-OVS-SIT VM image is designed to be minimalistic, small and efficient.
For that reason it is NOT build around any established Linux distribution
(Ubuntu, Red Hat, ...), but around "buildroot" (https://buildroot.org/)
which is aimed at building small Linux images for embedded systems.

Scripts in this directory are aimed at producing functionally identical VM
images each time they are run. That is, a given version of this package
will consistenly download the same buildroot version, and install the same
packages and the same kernel version with the same config.


### Prerequisites

This scripts have been tested on Ubuntu Linux. They should run on any platform
supported by buildroot, and where a standard bourne shell and Linux toolchain
are available.

## Files

### requirements.sh

(One-time) installs required Ubuntu packages for buildroot


### build.sh

Downloads all required packages source code and builds the VM image.
Is NOT intended to be run as root, but requires "sudo" privileges for a
handful of commands.

### clean.sh

Remove any object files and compiled files. Keep the downloaded source
packages, both of buildroot itself as well as any packages downloaded by
buildroot.

### deepclean.sh

Remove any compiled or downloaded files.

### CHANGELOG

A change log. This will also be copied onto the image itself.
Versions in the changelog MUST be tagged as follows:

~~~
## [MAJOR.MINOR] YYYY-MM-DD
~~~
eg.

~~~
## [1.0] 2021-11-01
~~~

This format will be used for auto-extracting the version
number, which will become part of the target image filename
and will also be copied onto the image itself.

### release-images
Contains pre-built VM images to avoid waiting for the build process
which is time consuming depending on your network and build machine.
