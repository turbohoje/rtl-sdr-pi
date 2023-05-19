# rtl-sdr-pi
power meter reading

### hardware
1. raspberry pi 3b+
1. [sdr tv card](https://www.amazon.com/NooElec-RTL-SDR-RTL2832U-Software-Packages/dp/B008S7AVTC/)

### tl/dr install notes


- install/compile [rtl-sdr](https://osmocom.org/projects/rtl-sdr/wiki/Rtl-sdr).
  - commands in the doc look like
    - cd rtl-sdr/
    -  mkdir build 
    - cd build
    -  cmake ../ -DINSTALL_UDEV_RULES=ON
    -  make
    -  sudo make install
    -  sudo ldconfig
  - blacklist an additional module
    - vim /etc/modprobe.d/blacklist-rtl8xxxu.conf
    - add `blacklist dvb_usb_rtl28xxu` 
- install one of the following
  - bemasher's rtlamr `go get github.com/bemasher/rtlamr` (go < 1.16 that comes with raspian)
  - https://github.com/turbohoje/rtlamr-prometheus
### to test
- on window run `rtl_tcp`
- in another run `rtlamr -filterid=98883030,3806796 -msgtype=scm,scm+` 


### meters
Type 4: ?? water ??

SCM Type 7: electrical

SCM+ Type 156: gas


#### filter id 3806796
![electric](img/electrical.jpg)

#### filter id 65560195
![gas](img/gas.png)