# pynqz2
Using Pynq Z2 board for FW / SW development

Start by download the standard OS for Pynq Z2. This is is currently version is 3.0.1, which is Ubuntu 22.04 based.
Download it from [The Pynq support site](https://www.pynq.io/boards.html) or directly [here](https://bit.ly/pynqz2_v3_0_1). This will give you a ZIP file, with an image (pynq_z2_v3.0.1.img) inside.
Flash this image to an SD card (min 8 Gb).

Steps:
- Insert the SD card
- Check that the jumper on the right is set to SD, not QSPI or JTAG
- Connect the USB cable
- Connect the power cable
- Connect the network cable (it can be connected anywhere on your network, it will automatically request a IP address)
- Switch on the board
- Locate the serial device on your PC and assign it to a terminal (e.g. Teraterm)

The board will boot, and show the following boot output:

```text
U-Boot 2022.01 (Apr 04 2022 - 07:53:54 +0000)

CPU:   Zynq 7z020
Silicon: v3.1
DRAM:  ECC disabled 512 MiB
Flash: 0 Bytes
NAND:  0 MiB
MMC:   mmc@e0100000: 0
Loading Environment from FAT... *** Error - No Valid Environment Area found
*** Warning - bad env area, using default environment

In:    serial@e0000000
Out:   serial@e0000000
Err:   serial@e0000000
Net:
ZYNQ GEM: e000b000, mdio bus e000b000, phyaddr -1, interface rgmii-id
SF: Detected s25fl128s with page size 256 Bytes, erase size 64 KiB, total 16 MiB
eth0: ethernet@e000b000
Hit any key to stop autoboot:  0
switch to partitions #0, OK
mmc0 is current device
Scanning mmc 0:1...
Found U-Boot script /boot.scr
2776 bytes read in 10 ms (270.5 KiB/s)
## Executing script at 03000000
Trying to load boot images from mmc0
6464328 bytes read in 366 ms (16.8 MiB/s)
## Loading kernel from FIT Image at 10000000 ...
   Using 'conf-1' configuration
   Verifying Hash Integrity ... OK
   Trying 'kernel-0' kernel subimage
     Description:  Linux Kernel
     Type:         Kernel Image
     Compression:  uncompressed
     Data Start:   0x100000d4
     Data Size:    6442720 Bytes = 6.1 MiB
     Architecture: ARM
     OS:           Linux
     Load Address: 0x00080000
     Entry Point:  0x00080000
     Hash algo:    sha1
     Hash value:   b056acb229d05b806f975396dacae4ad04002e0c
   Verifying Hash Integrity ... sha1+ OK
## Loading fdt from FIT Image at 10000000 ...
   Using 'conf-1' configuration
   Verifying Hash Integrity ... OK
   Trying 'fdt-0' fdt subimage
     Description:  Flattened Device Tree blob
     Type:         Flat Device Tree
     Compression:  uncompressed
     Data Start:   0x106250a8
     Data Size:    19792 Bytes = 19.3 KiB
     Architecture: ARM
     Hash algo:    sha1
     Hash value:   c20e513daf724f7b1b134fa9af089b026612751e
   Verifying Hash Integrity ... sha1+ OK
   Booting using the fdt blob at 0x106250a8
   Loading Kernel Image
   Loading Device Tree to 1ead4000, end 1eadbd4f ... OK

Starting kernel ...

Booting Linux on physical CPU 0x0
Linux version 5.15.19-xilinx-v2022.1 (oe-user@oe-host) (arm-xilinx-linux-gnueabi-gcc (GCC) 11.2.0, GNU ld (GNU Binutils) 2.37.20210721) #1 SMP PREEMPT Mon Apr 11 17:52:14 UTC 2022
CPU: ARMv7 Processor [413fc090] revision 0 (ARMv7), cr=18c5387d
CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
OF: fdt: Machine model: xlnx,zynq-7000
Memory policy: Data cache writealloc
cma: Reserved 128 MiB at 0x16800000
Zone ranges:
  Normal   [mem 0x0000000000000000-0x000000001fffffff]
  HighMem  empty
Movable zone start for each node
Early memory node ranges
  node   0: [mem 0x0000000000000000-0x000000001fffffff]
Initmem setup node 0 [mem 0x0000000000000000-0x000000001fffffff]
percpu: Embedded 12 pages/cpu s18828 r8192 d22132 u49152
Built 1 zonelists, mobility grouping on.  Total pages: 129920
Kernel command line: root=/dev/mmcblk0p2 rw earlyprintk rootfstype=ext4 rootwait devtmpfs.mount=1 uio_pdrv_genirq.of_id="generic-uio" clk_ignore_unused
Unknown kernel command line parameters "earlyprintk", will be passed to user space.
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes, linear)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes, linear)
mem auto-init: stack:off, heap alloc:off, heap free:off
Memory: 373332K/524288K available (9216K kernel code, 324K rwdata, 2512K rodata, 1024K init, 296K bss, 19884K reserved, 131072K cma-reserved, 0K highmem)
rcu: Preemptible hierarchical RCU implementation.
rcu:    RCU event tracing is enabled.
rcu:    RCU restricting CPUs from NR_CPUS=4 to nr_cpu_ids=2.
        Trampoline variant of Tasks RCU enabled.
        Tracing variant of Tasks RCU enabled.
rcu: RCU calculated value of scheduler-enlistment delay is 10 jiffies.
rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
NR_IRQS: 16, nr_irqs: 16, preallocated irqs: 16
efuse mapped to (ptrval)
slcr mapped to (ptrval)
GIC physical location is 0xf8f01000
L2C: platform modifies aux control register: 0x72360000 -> 0x72760000
L2C: DT/platform modifies aux control register: 0x72360000 -> 0x72760000
L2C-310 erratum 769419 enabled
L2C-310 enabling early BRESP for Cortex-A9
L2C-310 full line of zeros enabled for Cortex-A9
L2C-310 ID prefetch enabled, offset 1 lines
L2C-310 dynamic clock gating enabled, standby mode enabled
L2C-310 cache controller enabled, 8 ways, 512 kB
L2C-310: CACHE_ID 0x410000c8, AUX_CTRL 0x76760001
random: get_random_bytes called from start_kernel+0x364/0x5f8 with crng_init=0
zynq_clock_init: clkc starts at (ptrval)
Zynq clock init
sched_clock: 64 bits at 162MHz, resolution 6ns, wraps every 4398046511101ns
clocksource: arm_global_timer: mask: 0xffffffffffffffff max_cycles: 0x257a3bfb55, max_idle_ns: 440795207830 ns
Switching to timer-based delay loop, resolution 6ns
Console: colour dummy device 80x30
printk: console [tty0] enabled
Calibrating delay loop (skipped), value calculated using timer frequency.. 325.00 BogoMIPS (lpj=1625000)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 1024 (order: 0, 4096 bytes, linear)
Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes, linear)
CPU: Testing write buffer coherency: ok
CPU0: Spectre v2: using BPIALL workaround
CPU0: thread -1, cpu 0, socket 0, mpidr 80000000
Setting up static identity map for 0x100000 - 0x100060
rcu: Hierarchical SRCU implementation.
smp: Bringing up secondary CPUs ...
CPU1: thread -1, cpu 1, socket 0, mpidr 80000001
CPU1: Spectre v2: using BPIALL workaround
smp: Brought up 1 node, 2 CPUs
SMP: Total of 2 processors activated (650.00 BogoMIPS).
CPU: All CPU(s) started in SVC mode.
devtmpfs: initialized
VFP support v0.3: implementor 41 architecture 3 part 30 variant 9 rev 4
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
futex hash table entries: 512 (order: 3, 32768 bytes, linear)
pinctrl core: initialized pinctrl subsystem
NET: Registered PF_NETLINK/PF_ROUTE protocol family
DMA: preallocated 256 KiB pool for atomic coherent allocations
thermal_sys: Registered thermal governor 'step_wise'
cpuidle: using governor menu
amba f8801000.etb: Fixing up cyclic dependency with replicator
amba f8803000.tpiu: Fixing up cyclic dependency with replicator
amba f8804000.funnel: Fixing up cyclic dependency with replicator
amba f889c000.ptm: Fixing up cyclic dependency with f8804000.funnel
amba f889d000.ptm: Fixing up cyclic dependency with f8804000.funnel
hw-breakpoint: found 5 (+1 reserved) breakpoint and 1 watchpoint registers.
hw-breakpoint: maximum watchpoint size is 4 bytes.
zynq-ocm f800c000.ocmc: ZYNQ OCM pool: 256 KiB @ 0x(ptrval)
e0000000.serial: ttyPS0 at MMIO 0xe0000000 (irq = 34, base_baud = 6250000) is a xuartps
printk: console [ttyPS0] enabled
raid6: int32x8  gen()   117 MB/s
raid6: int32x8  xor()    78 MB/s
raid6: int32x4  gen()   125 MB/s
raid6: int32x4  xor()    88 MB/s
raid6: int32x2  gen()   200 MB/s
raid6: int32x2  xor()   125 MB/s
raid6: int32x1  gen()   179 MB/s
raid6: int32x1  xor()   100 MB/s
raid6: using algorithm int32x2 gen() 200 MB/s
raid6: .... xor() 125 MB/s, rmw enabled
raid6: using intx1 recovery algorithm
vgaarb: loaded
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
mc: Linux media interface: v0.10
videodev: Linux video capture interface: v2.00
pps_core: LinuxPPS API ver. 1 registered
pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
PTP clock support registered
EDAC MC: Ver: 3.0.0
FPGA manager framework
Advanced Linux Sound Architecture Driver Initialized.
clocksource: Switched to clocksource arm_global_timer
NET: Registered PF_INET protocol family
IP idents hash table entries: 8192 (order: 4, 65536 bytes, linear)
tcp_listen_portaddr_hash hash table entries: 512 (order: 0, 6144 bytes, linear)
TCP established hash table entries: 4096 (order: 2, 16384 bytes, linear)
TCP bind hash table entries: 4096 (order: 3, 32768 bytes, linear)
TCP: Hash tables configured (established 4096 bind 4096)
UDP hash table entries: 256 (order: 1, 8192 bytes, linear)
UDP-Lite hash table entries: 256 (order: 1, 8192 bytes, linear)
NET: Registered PF_UNIX/PF_LOCAL protocol family
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
PCI: CLS 0 bytes, default 64
armv7-pmu f8891000.pmu: hw perfevents: no interrupt-affinity property, guessing.
hw perfevents: enabled with armv7_cortex_a9 PMU driver, 7 counters available
Initialise system trusted keyrings
workingset: timestamp_bits=14 max_order=17 bucket_order=3
squashfs: version 4.0 (2009/01/31) Phillip Lougher
jffs2: version 2.2. (NAND) (SUMMARY)  © 2001-2006 Red Hat, Inc.
xor: measuring software checksum speed
   arm4regs        :  1045 MB/sec
   8regs           :   805 MB/sec
   32regs          :   836 MB/sec
xor: using function: arm4regs (1045 MB/sec)
Key type asymmetric registered
Asymmetric key parser 'x509' registered
io scheduler mq-deadline registered
io scheduler kyber registered
zynq-pinctrl 700.pinctrl: zynq pinctrl initialized
dma-pl330 f8003000.dmac: Loaded driver for PL330 DMAC-241330
dma-pl330 f8003000.dmac:        DBUFF-128x8bytes Num_Chans-8 Num_Peri-4 Num_Events-16
brd: module loaded
loop: module loaded
spi_master spi0: cannot find modalias for /axi/spi@e000d000/flash@0
spi_master spi0: Failed to create SPI device for /axi/spi@e000d000/flash@0
tun: Universal TUN/TAP device driver, 1.6
CAN device driver interface
macb e000b000.ethernet eth0: Cadence GEM rev 0x00020118 at 0xe000b000 irq 36 (00:00:05:6b:04:20)
e1000e: Intel(R) PRO/1000 Network Driver
e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci-pci: EHCI PCI platform driver
usbcore: registered new interface driver cdc_acm
cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
usbcore: registered new interface driver cdc_wdm
usbcore: registered new interface driver usb-storage
usbcore: registered new interface driver usbserial_generic
usbserial: USB Serial support registered for generic
usbcore: registered new interface driver usb_serial_simple
usbserial: USB Serial support registered for carelink
usbserial: USB Serial support registered for zio
usbserial: USB Serial support registered for funsoft
usbserial: USB Serial support registered for flashloader
usbserial: USB Serial support registered for google
usbserial: USB Serial support registered for libtransistor
usbserial: USB Serial support registered for vivopay
usbserial: USB Serial support registered for moto_modem
usbserial: USB Serial support registered for motorola_tetra
usbserial: USB Serial support registered for novatel_gps
usbserial: USB Serial support registered for hp4x
usbserial: USB Serial support registered for suunto
usbserial: USB Serial support registered for siemens_mpi
ULPI transceiver vendor/product ID 0x0451/0x1507
Found TI TUSB1210 ULPI transceiver.
ULPI integrity check: passed.
ci_hdrc ci_hdrc.0: EHCI Host Controller
ci_hdrc ci_hdrc.0: new USB bus registered, assigned bus number 1
ci_hdrc ci_hdrc.0: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
i2c_dev: i2c /dev entries driver
cdns-i2c e0004000.i2c: 100 kHz mmio e0004000 irq 30
cdns-i2c e0005000.i2c: 100 kHz mmio e0005000 irq 31
cdns-wdt f8005000.watchdog: Xilinx Watchdog Timer with timeout 10s
device-mapper: ioctl: 4.45.0-ioctl (2021-03-22) initialised: dm-devel@redhat.com
EDAC MC: ECC not enabled
Xilinx Zynq CpuIdle Driver started
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pltfm: SDHCI platform and OF driver helper
ledtrig-cpu: registered to indicate activity on CPUs
clocksource: ttc_clocksource: mask: 0xffff max_cycles: 0xffff, max_idle_ns: 551318127 ns
timer #0 at (ptrval), irq=49
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
xlnk xlnk: Major 243
xlnk xlnk: xlnk driver loaded
xlnk xlnk: xlnk_pdev is not null
fpga_manager fpga0: Xilinx Zynq FPGA Manager registered
mmc0: SDHCI controller on e0100000.mmc [e0100000.mmc] using ADMA
IPVS: Registered protocols (TCP, UDP)
IPVS: Connection hash table configured (size=4096, memory=32Kbytes)
IPVS: ipvs loaded.
IPVS: [rr] scheduler registered.
Initializing XFRM netlink socket
NET: Registered PF_INET6 protocol family
Segment Routing with IPv6
In-situ OAM (IOAM) with IPv6
sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
NET: Registered PF_PACKET protocol family
mmc0: new high speed SDHC card at address aaaa
can: controller area network core
mmcblk0: mmc0:aaaa SC16G 14.8 GiB
NET: Registered PF_CAN protocol family
can: raw protocol
can: broadcast manager protocol
 mmcblk0: p1 p2
can: netlink gateway - max_hops=1
Registering SWP/SWPB emulation handler
Loading compiled-in X.509 certificates
Btrfs loaded, crc32c=crc32c-generic, zoned=no, fsverity=no
of-fpga-region fpga-full: FPGA Region probed
of_cfs_init
of_cfs_init: OK
cfg80211: Loading compiled-in X.509 certificates for regulatory database
cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
clk: Not disabling unused clocks
cfg80211: failed to load regulatory.db
ALSA device list:
  No soundcards found.
EXT4-fs (mmcblk0p2): mounted filesystem with ordered data mode. Opts: (null). Quota mode: disabled.
VFS: Mounted root (ext4 filesystem) on device 179:2.
devtmpfs: mounted
Freeing unused kernel image (initmem) memory: 1024K
Run /sbin/init as init process
random: fast init done
systemd[1]: System time before build time, advancing clock.
systemd[1]: Failed to find module 'autofs4'
systemd[1]: systemd 249.11-0ubuntu3 running in system mode (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS -OPENSSL +ACL +BLKID +CURL +ELFUTILS -FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP -LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)
systemd[1]: Detected architecture arm.

Welcome to PynqLinux, based on Ubuntu 22.04!

systemd[1]: Hostname set to <pynq>.
systemd[1]: Queued start job for default target Multi-User System.
random: systemd: uninitialized urandom read (16 bytes read)
systemd[1]: Created slice Slice /system/modprobe.
[  OK  ] Created slice Slice /system/modprobe.
random: systemd: uninitialized urandom read (16 bytes read)
systemd[1]: Created slice Slice /system/serial-getty.
[  OK  ] Created slice Slice /system/serial-getty.
random: systemd: uninitialized urandom read (16 bytes read)
systemd[1]: Created slice User and Session Slice.
[  OK  ] Created slice User and Session Slice.
systemd[1]: Started Dispatch Password Requests to Console Directory Watch.
[  OK  ] Started Dispatch Password …ts to Console Directory Watch.
systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[  OK  ] Started Forward Password R…uests to Wall Directory Watch.
systemd[1]: Condition check resulted in Arbitrary Executable File Formats File System Automount Point being skipped.
systemd[1]: Reached target Local Encrypted Volumes.
[  OK  ] Reached target Local Encrypted Volumes.
systemd[1]: Reached target Remote File Systems.
[  OK  ] Reached target Remote File Systems.
systemd[1]: Reached target Slice Units.
[  OK  ] Reached target Slice Units.
systemd[1]: Reached target Local Verity Protected Volumes.
[  OK  ] Reached target Local Verity Protected Volumes.
systemd[1]: Listening on Syslog Socket.
[  OK  ] Listening on Syslog Socket.
systemd[1]: Listening on initctl Compatibility Named Pipe.
[  OK  ] Listening on initctl Compatibility Named Pipe.
systemd[1]: Condition check resulted in Journal Audit Socket being skipped.
systemd[1]: Listening on Journal Socket (/dev/log).
[  OK  ] Listening on Journal Socket (/dev/log).
systemd[1]: Listening on Journal Socket.
[  OK  ] Listening on Journal Socket.
systemd[1]: Listening on udev Control Socket.
[  OK  ] Listening on udev Control Socket.
systemd[1]: Listening on udev Kernel Socket.
[  OK  ] Listening on udev Kernel Socket.
systemd[1]: Condition check resulted in Huge Pages File System being skipped.
systemd[1]: Mounting POSIX Message Queue File System...
         Mounting POSIX Message Queue File System...
systemd[1]: Mounting Kernel Debug File System...
         Mounting Kernel Debug File System...
systemd[1]: Condition check resulted in Kernel Trace File System being skipped.
systemd[1]: Starting Journal Service...
         Starting Journal Service...
systemd[1]: Starting Restore / save the current clock...
         Starting Restore / save the current clock...
systemd[1]: Starting Set the console keyboard layout...
         Starting Set the console keyboard layout...
systemd[1]: Condition check resulted in Create List of Static Device Nodes being skipped.
systemd[1]: Starting Load Kernel Module configfs...
         Starting Load Kernel Module configfs...
systemd[1]: Starting Load Kernel Module drm...
         Starting Load Kernel Module drm...
systemd[1]: Starting Load Kernel Module fuse...
         Starting Load Kernel Module fuse...
systemd[1]: Started Nameserver information manager.
[  OK  ] Started Nameserver information manager.
systemd[1]: Reached target Preparation for Network.
[  OK  ] Reached target Preparation for Network.
systemd[1]: Starting Load Kernel Modules...
         Starting Load Kernel Modules...
systemd[1]: Starting Remount Root and Kernel File Systems...
         Starting Remount Root and Kernel File Systems...
systemd[1]: Starting Coldplug All udev Devices...
         Starting Coldplug All udev Devices...
systemd[1]: Started Journal Service.
[  OK  ] Started Journal Service.
[  OK  ] Mounted POSIX Message Queue File System.
[  OK  ] Mounted Kernel Debug File System.
[  OK  ] Finished Restore / save the current clock.
[  OK  ] Finished Load Kernel Module configfs.
[  OK  ] Finished Load Kernel Module drm.
[  OK  ] Finished Set the console keyboard layout.
[  OK  ] Finished Load Kernel Module fuse.
[  OK  ] Finished Load Kernel Modules.
[  OK  ] Finished Remount Root and Kernel File Systems.
         Activating swap /var/swap...
         Mounting Kernel Configuration File System...
Adding 524284k swap on /var/swap.  Priority:-2 extents:1 across:524284k SS
         Starting Flush Journal to Persistent Storage...
systemd-journald[110]: Received client request to flush runtime journal.
         Starting Load/Save Random Seed...
systemd-journald[110]: File /var/log/journal/b4e19d1e11f24633a2f2e1fe2798cbe4/system.journal corrupted or uncleanly shut down, renaming and replacing.
         Starting Apply Kernel Variables...
         Starting Create System Users...
[  OK  ] Activated swap /var/swap.
[  OK  ] Mounted Kernel Configuration File System.
[  OK  ] Reached target Swaps.
[  OK  ] Finished Apply Kernel Variables.
[  OK  ] Finished Create System Users.
         Starting Create Static Device Nodes in /dev...
[  OK  ] Finished Coldplug All udev Devices.
         Starting Helper to synchronize boot up for ifupdown...
[  OK  ] Finished Flush Journal to Persistent Storage.
[  OK  ] Finished Create Static Device Nodes in /dev.
[  OK  ] Reached target Preparation for Local File Systems.
[  OK  ] Reached target Local File Systems.
         Starting Enable support fo…l executable binary formats...
         Starting Set console font and keymap...
         Starting Create Volatile Files and Directories...
         Starting Rule-based Manage…for Device Events and Files...
[  OK  ] Finished Enable support fo…nal executable binary formats.
[  OK  ] Finished Set console font and keymap.
[  OK  ] Finished Create Volatile Files and Directories.
[  OK  ] Started Entropy Daemon based on the HAVEGE algorithm.
         Starting Network Name Resolution...
         Starting Network Time Synchronization...
         Starting Record System Boot/Shutdown in UTMP...
[  OK  ] Started Rule-based Manager for Device Events and Files.
[  OK  ] Finished Record System Boot/Shutdown in UTMP.
[  OK  ] Stopped Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Started Entropy Daemon based on the HAVEGE algorithm.
zocl-drm axi:zyxclmm_drm: IRQ index 0 not found
[  OK  ] Found device /dev/ttyPS0.
[  OK  ] Finished Helper to synchronize boot up for ifupdown.
[  OK  ] Started Network Time Synchronization.
[  OK  ] Finished Load/Save Random Seed.
[  OK  ] Reached target System Time Set.
[  OK  ] Reached target Hardware activated USB gadget.
[  OK  ] Stopped Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Started Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Reached target System Initialization.
[  OK  ] Started resolvconf-pull-resolved.path.
[  OK  ] Started Trigger to poll fo…y enabled on GCP LTS non-pro).
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Started Daily dpkg database backup timer.
[  OK  ] Started Periodic ext4 Onli…ata Check for All Filesystems.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Started Daily rotation of log files.
[  OK  ] Started Daily man-db regeneration.
[  OK  ] Started Message of the Day.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Started Ubuntu Advantage Timer for running repeated jobs.
[  OK  ] Reached target Path Units.
[  OK  ] Reached target Timer Units.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Reached target Socket Units.
[  OK  ] Reached target Basic System.
         Starting LSB: automatic crash report generation...
         Starting Executing boot.py from the boot partition...
[  OK  ] Started Regular background program processing daemon.
[  OK  ] Started D-Bus System Message Bus.
[  OK  ] Started Save initial kernel messages after boot.
         Starting Remove Stale Onli…t4 Metadata Check Snapshots...
[  OK  ] Started ifup for eth0.
         Starting Jupyter Notebook Server...
         Starting LSB: Load kernel …d to enable cpufreq scaling...
         Starting Dispatcher daemon for systemd-networkd...
         Starting Raise network interfaces...
         Starting Resize Filesystem on SD card...
         Starting System Logging Service...
         Starting User Login Management...
[  OK  ] Started Network Name Resolution.
[  OK  ] Finished Resize Filesystem on SD card.
[  OK  ] Started System Logging Service.
[  OK  ] Started LSB: automatic crash report generation.
[  OK  ] Reached target Host and Network Name Lookups.
[  OK  ] Stopped Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Started Entropy Daemon based on the HAVEGE algorithm.
         Starting resolvconf-pull-resolved.service...
[  OK  ] Started LSB: Load kernel m…ded to enable cpufreq scaling.
         Starting LSB: set CPUFreq kernel parameters...
[  OK  ] Started LSB: set CPUFreq kernel parameters.
[  OK  ] Finished Remove Stale Onli…ext4 Metadata Check Snapshots.
[  OK  ] Finished resolvconf-pull-resolved.service.
[  OK  ] Started User Login Management.
[  OK  ] Started Dispatcher daemon for systemd-networkd.
[  OK  ] Stopped Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Started Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Stopped Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Started Entropy Daemon based on the HAVEGE algorithm.
         Starting resolvconf-pull-resolved.service...
[  OK  ] Finished resolvconf-pull-resolved.service.
[  OK  ] Stopped Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Started Entropy Daemon based on the HAVEGE algorithm.
[  OK  ] Finished Raise network interfaces.
[  OK  ] Reached target Network.
[  OK  ] Reached target Network is Online.
[  OK  ] Started ISC DHCP IPv4 server.
[  OK  ] Started ISC DHCP IPv6 server.
         Starting Samba NMB Daemon...
         Starting OpenBSD Secure Shell server...
         Starting Permit User Sessions...
[  OK  ] Started Unattended Upgrades Shutdown.
[  OK  ] Finished Permit User Sessions.
[  OK  ] Started Serial Getty on ttyPS0.
         Starting Set console scheme...
[  OK  ] Finished Set console scheme.
```

PYNQ uses a base.bit bitfile, which is located under /home/xilinx/pynq/overlays/base (actually) the pynq folder is a symlink to /usr/local/share/pynq-venv/lib/python3.10/site-packages/pynq.


```text
Creating a base bitstream for the PYNQ-Z2 board involves generating a hardware design using Xilinx Vivado and exporting it for use with the PYNQ framework. Below is a concise guide to help you through the process:

Steps to Create a Base Bitstream for PYNQ-Z2

Install Required Tools:

Install Xilinx Vivado (version compatible with PYNQ-Z2, e.g., 2020.2 or 2021.1).
Ensure you have the PYNQ repository cloned from GitHub.

Clone the PYNQ Repository:

Clone the official PYNQ GitHub repository:
Copy the code
git clone https://github.com/Xilinx/PYNQ.git
cd PYNQ/boards/Pynq-Z2/base


Set Up Vivado Project:

Open Vivado and create a new project.
Select the PYNQ-Z2 board as the target hardware.
Import the necessary IP cores and constraints files from the base folder in the PYNQ repository.

Add Design Sources:

Add the provided TCL scripts and block design files from the PYNQ repository.
Run the TCL script to generate the block design:
Copy the code
source base.tcl


Generate the Bitstream:

Validate the design in Vivado.
Synthesize and implement the design.
Generate the bitstream file (base.bit).

Export Hardware:

Export the hardware design along with the bitstream:
Copy the code
File > Export > Export Hardware

Include the .hwh file for PYNQ compatibility.

Copy Files to PYNQ-Z2:

Transfer the generated base.bit and base.hwh files to the PYNQ-Z2 board (e.g., via SCP or USB).
Place them in the /home/xilinx/pynq/overlays/base/ directory.

Test the Bitstream:

On the PYNQ-Z2 board, load the bitstream using Python:
Copy the code
from pynq import Overlay
base = Overlay("/home/xilinx/pynq/overlays/base/base.bit")
base.download()

Tips:
Ensure all IP cores are compatible with the Vivado version you're using.
Use the PYNQ-Z2 board files provided in the PYNQ repository for accurate constraints.
If errors occur, check the Vivado logs for missing dependencies or incorrect configurations.

This process will create a functional base bitstream for the PYNQ-Z2 board, enabling you to use it with the PYNQ framework for further development.
```