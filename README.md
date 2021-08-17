Arch Linux modified kernel for MacBooks
==============
**Current kernel version:** 5.13.10

An Arch Linux package for Linux kernel with bleeding edge 2018+ MacBook Pro support.  
This is a modified version of [aunali1's linux-mbp-arch kernel](https://github.com/aunali1/linux-mbp-arch), applying the
Corellium patch for BCM4377 and other chips.

In order to get the patch to apply cleanly, some patches to support other BCMxxxx devices from other MacBooks.
The following devices have been tested to work with this kernel:
- `MacBookAir9,1` (MacBook Air, 2020, Intel) - wireless chip `BCM4377b`/`BCM4377/4`
- `MacBookPro16,1` (MacBook Pro, 2019, Intel) - wireless chip `BCM4364`

Based on work from the [t2linux wiki](https://wiki.t2linux.org).

## Installation
You can choose to build it manually, or use the prebuilt package from the GitHub workflow.
### Prebuilt
Download the latest `mbp-16.1-linux-wifi-arch` archive from the **Artifacts** section of the latest [GitHub Actions run](https://github.com/jamlam/mbp-16.1-linux-wifi/actions), and unzip it to your desktop.  

  
Install the kernel, docss, and headers using the following command and it should copy the kernel to your `boot` automatically.
```
sudo pacman -U mbp-16.1-linux-wifi-*.zst
```
### Manual compilation
Clone the repo and build it using `makepkg`.
```bash
git clone https://github.com/jamlam/mbp-16.1-linux-wifi.git
cd mbp-16.1-linux-wifi.git
MAKEFLAGS="-j$(nproc)" # This should tell makepkg to use as many processors as are available
makepkg -si --skipinteg
```
This can take a while.
