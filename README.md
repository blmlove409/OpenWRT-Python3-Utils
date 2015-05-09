# OpenWRT-Python3.4-Tornado
Python 3.4 Tornado 4.1 Makefile for OpenWRT

## Dependencies:

* libcurl
* python3
* libc  (required for python3.4 because it contains the definiton for posix_fallocate64)

## How to Install:

1. Add to your `openwrt/feeds.conf.default` file: `src-git tornado https://github.com/NucleaPeon/OpenWRT-Python3.4-Tornado.git`
2. Update your feeds: `./scripts/feeds update -a` (or `./scripts/feeds update tornado`)
3. Install packages from your feeds (I've found this way works, but isn't necessarily recommended): `./scripts/feeds install -a`
 
### Install via Image:
4. Run `make menuconfig`
5. Enter `Languages --> Python -->` and select `python3` and `python3-tornado` to build with your image

or

### Install via Modules/Packages
4. Run `make package/python3` and `make package/python3-tornado`
 
## Advice:

During testing of this Makefile, I have ran into the issue where the md5sum is not correct, even though it worked previously, so it will download and fail to install.

To correct this issue, change the `Makefile` md5sum line to the current tornado-4.1.tar.gz file:
1. Download the `https://pypi.python.org/packages/source/t/tornado/tornado-4.1.tar.gz` file. 
2. Run `md5sum tornado-4.1.tar.gz` on it
3. Take the resulting md5sum and replace the `PKG_MD5SUM:=...` line and copy the new one in. 

The maintainers of tornado may replace the tornado-4.1.tar.gz file with newer 4.1 builds with the same filename resulting in a new md5sum from time to time, but that's just my assumption.