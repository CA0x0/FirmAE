# FirmAE

FirmAE is a fully-automated framework that performs emulation and vulnerability analysis. FirmAE significantly increases the emulation success rate (From [Firmadyne](https://github.com/firmadyne/firmadyne)'s 16.28% to 79.36%) with five arbitration techniques. We tested FirmAE on 1,124 wireless-router and IP-camera firmware images from top eight vendors.

We also developed a dynamic analysis tool for 0-day discovery, which infers web service information based on the filesystem and kernel logs of target firmware.
By running our tool on the succesfully emulation firmware images, we discovered 12 new 0-days which affect 23 devices.

# Installation

Note that we tested FirmAE on Ubuntu 18.04.

1. Clone `FirmAE`
```
$ git clone --recursive https://github.com/pr0v3rbs/FirmAE
```

2. Run `download.sh` script.
```
$ ./download.sh
```

3. Run `install.sh` script.
```
$ ./install.sh
```

4. Run `init.sh` script.
```
$ ./init.sh
```

# Usage

1. Prepare a firmware.

```
$ wget ftp://ftp.dlink.eu/Products/dir/dir-868l/driver_software/DIR-868L_fw_revB_2-05b02_eu_multi_20161117.zip
```

2. Check emulation
```
$ sudo ./run.sh -c <brand> <firmware>
```

3. Run analysis
```
$ sudo ./run.sh -a <brand> <firmware>
```

## Parallel mode

First, prepare a docker image.
```
$ sudo ./docker-init.sh
```

Then, run one of the below commands. ```-ec``` checks only the emulation, and ```-ea``` checks the emulation and analyzes vulnerabilities.
```
$ sudo ./docker-helper.py -ec <brand> <firmware>
$ sudo ./docker-helper.py -ea <brand> <firmware>
```

# CVEs

- ASUS: [CVE-2019-20082](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2019-20082)
- Belkin: [Belkin01](https://github.com/pr0v3rbs/CVE/tree/master/Belkin01)
- D-Link: [CVE-2018-20114](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2018-20114), [CVE-2018-19986](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2018-19986%20-%2019990#cve-2018-19986---hnap1setroutersettings), [CVE-2018-19987](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2018-19986%20-%2019990#cve-2018-19987---hnap1setaccesspointmode), [CVE-2018-19988](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2018-19986%20-%2019990#cve-2018-19988---hnap1setclientinfodemo), [CVE-2018-19989](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2018-19986%20-%2019990#cve-2018-19989---hnap1setqossettings), [CVE-2018-19990](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2018-19986%20-%2019990#cve-2018-19990---hnap1setwifiverifyalpha), [CVE-2019-6258](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2019-6258), [CVE-2019-20084](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2019-20084)
- TRENDNet: [CVE-2019-11399](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2019-11399), [CVE-2019-11400](https://github.com/pr0v3rbs/CVE/tree/master/CVE-2019-11400)

# Authors
This research project has been conducted by [SysSec Lab](https://syssec.kr) at KAIST.
* [Mingeun Kim](https://pr0v3rbs.blogspot.kr/)
* [Dongkwan Kim](https://0xdkay.me/)
* [Eunsoo Kim](https://hahah.kim)
* [Suryeon Kim](#)
* [Yeongjin Jang](https://www.unexploitable.systems/)
* [Yongdae Kim](https://syssec.kaist.ac.kr/~yongdaek/)

# Citation
We would appreciate if you consider citing [our paper](https://syssec.kaist.ac.kr/pub/2020/kim_acsac2020.pdf) when using FirmAE.
```bibtex
@inproceedings{kim:2020:firmae,
  author = {Mingeun Kim and Dongkwan Kim and Eunsoo Kim and Suryeon Kim and Yeongjin Jang and Yongdae Kim},
  title = {{FirmAE}: Towards Large-Scale Emulation of IoT Firmware for Dynamic Analysis},
  booktitle = {Annual Computer Security Applications Conference (ACSAC)},
  year = 2020,
  month = dec,
  address = {Online}
}
```
