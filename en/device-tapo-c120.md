# OpenIPC Wiki
[Table of Content](../README.md)

## TP-Link Tapo C120 (v1.6)
### GPIO
IRLed  | WhiteLed | RedLed  | GreenLed | Speaker | Reset  | IRCut
-|-|-|-|-|-|-
GPIO12 | GPIO14   | GPIO10  | GPIO11   | GPIO61? | GPIO25 | GPIO81

- 10 red
- 11 green
- 12 ir
- 13 ir
- 14 white
- 22? padmux sdcard?
- 25 crash
- 42 wifi
- 81 ircut 

#### /etc/isp.config
```
"ir_cut_gpio_num":81,
"ir_led_double_gpio_ports":[12,13],
```

```
cli -s .nightMode.irCutPin1 78
cli -s .nightMode.backlightPin 14
cli -s .audio.speakerPin 61
```

### I2C
```
i2c-1   i2c             Sstar I2C adapter 1                     I2C adapter
i2c-2   i2c             Sstar I2C adapter 2                     I2C adapter
i2c-0   i2c             Sstar I2C adapter 0                     I2C adapter
```
- /dev/i2c-1 only has 0x30
```
00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
30: 00 00 01 00 00 00 80 00 00 ff 00 00 00 00 10 00    ..?...?.......?.
40: 00 00 00 00 00 00 00 00 6b 00 00 00 00 00 00 00    ........k.......
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
80: 45 00 61 a0 ff ff ff a1 32 04 0a ff 00 00 00 00    E.a?...?2??.....
90: 00 00 00 00 00 00 00 47 43 39 55 32 32 01 00 06    .......GC9U22?.?
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
```

### Wireless
```
fw_setenv wlandev rtl8188fu-generic
fw_setenv wlanssid Router
fw_setenv wlanpass 12345678
```

### RegInfo
```
muxctrl_reg0 0x1f207c00 0xac0 PAD_SD1_IO1
muxctrl_reg1 0x1f207c04 0xac0 PAD_SD1_IO0
muxctrl_reg2 0x1f207c08 0x2d0 PAD_SD1_IO5
muxctrl_reg3 0x1f207c0c 0x2c0 PAD_SD1_IO4
muxctrl_reg4 0x1f207c10 0x2c0 PAD_SD1_IO3
muxctrl_reg5 0x1f207c14 0xac0 PAD_SD1_IO2
muxctrl_reg6 0x1f207c18 0xa55 PAD_SD1_IO6
muxctrl_reg7 0x1f207c1c 0xa55 PAD_UART1_RX
muxctrl_reg8 0x1f207c20 0xa55 PAD_UART1_TX
muxctrl_reg9 0x1f207c24 0xa55 PAD_SPI0_CZ
muxctrl_reg10 0x1f207c28 0xa54 PAD_SPI0_CK
muxctrl_reg11 0x1f207c2c 0xa55 PAD_SPI0_DI
muxctrl_reg12 0x1f207c30 0x255 PAD_SPI0_DO
muxctrl_reg13 0x1f207c34 0x264 PAD_PWM0
muxctrl_reg14 0x1f207c38 0x254 PAD_PWM1
muxctrl_reg15 0x1f207c3c 0x254 PAD_SD_CLK
muxctrl_reg16 0x1f207c40 0xa55 PAD_SD_CMD
muxctrl_reg17 0x1f207c44 0xa55 PAD_SD_D0
muxctrl_reg18 0x1f207c48 0xa55 PAD_SD_D1
muxctrl_reg19 0x1f207c4c 0xa55 PAD_SD_D2
muxctrl_reg20 0x1f207c50 0xa55 PAD_SD_D3
muxctrl_reg21 0x1f207c54 0xa55 PAD_USB_CID
muxctrl_reg22 0x1f207c58 0xa5c PAD_PM_SD_CDZ
muxctrl_reg23 0x1f207c5c 0xa55 PAD_PM_IRIN
muxctrl_reg24 0x1f207c64 0xa55 PAD_PM_UART_RX
muxctrl_reg25 0x1f207c68 0xa54 PAD_PM_UART_TX
muxctrl_reg26 0x1f207c6c 0xa54 PAD_PM_GPIO0
muxctrl_reg27 0x1f207c70 0xa54 PAD_PM_GPIO1
muxctrl_reg28 0x1f207c74 0xa54 PAD_PM_GPIO2
muxctrl_reg29 0x1f207c78 0xa54 PAD_PM_GPIO3
muxctrl_reg30 0x1f207c7c 0xa55 PAD_PM_GPIO4
muxctrl_reg31 0x1f207c80 0xa5b PAD_PM_GPIO7
muxctrl_reg32 0x1f207c84 0xa58 PAD_PM_GPIO8
muxctrl_reg33 0x1f207c88 0x25b PAD_PM_GPIO9
muxctrl_reg34 0x1f207c8c 0x2d5 PAD_PM_SPI_CZ
muxctrl_reg35 0x1f207c90 0x2e4 PAD_PM_SPI_DI
muxctrl_reg36 0x1f207c94 0x2d5 PAD_PM_SPI_WPZ
muxctrl_reg37 0x1f207c98 0xad5 PAD_PM_SPI_DO
muxctrl_reg38 0x1f207c9c 0xad4 PAD_PM_SPI_CK
muxctrl_reg39 0x1f207ca0 0x2d5 PAD_PM_SPI_HLD
muxctrl_reg40 0x1f207ca4 0x264 PAD_PM_LED0
muxctrl_reg41 0x1f207ca8 0x254 PAD_PM_LED1
muxctrl_reg42 0x1f207cc4 0xa65 PAD_FUART_RX
muxctrl_reg43 0x1f207cc8 0xa64 PAD_FUART_TX
muxctrl_reg44 0x1f207ccc 0xa55 PAD_FUART_CTS
muxctrl_reg45 0x1f207cd0 0xa58 PAD_FUART_RTS
muxctrl_reg46 0x1f207cd4 0xa55 PAD_GPIO0
muxctrl_reg47 0x1f207cd8 0xa55 PAD_GPIO1
muxctrl_reg48 0x1f207cdc 0xa65 PAD_GPIO2
muxctrl_reg49 0x1f207ce0 0xa65 PAD_GPIO3
muxctrl_reg50 0x1f207ce4 0xa65 PAD_GPIO4
muxctrl_reg51 0x1f207ce8 0xa65 PAD_GPIO5
muxctrl_reg52 0x1f207cec 0xa65 PAD_GPIO6
muxctrl_reg53 0x1f207cf0 0xa65 PAD_GPIO7
muxctrl_reg54 0x1f207cf4 0xa65 PAD_GPIO14
muxctrl_reg55 0x1f207cf8 0xa65 PAD_GPIO15
muxctrl_reg56 0x1f207cfc 0xa65 PAD_I2C0_SCL
muxctrl_reg57 0x1f207d00 0xa65 PAD_I2C0_SDA
muxctrl_reg58 0x1f207d04 0xa65 PAD_I2C1_SCL
muxctrl_reg59 0x1f207d08 0xa65 PAD_I2C1_SDA
muxctrl_reg60 0x1f207d0c 0x264 PAD_SR_IO00
muxctrl_reg61 0x1f207d10 0x264 PAD_SR_IO01
muxctrl_reg62 0x1f207d14 0x24 PAD_SR_IO02
muxctrl_reg63 0x1f207d18 0x24 PAD_SR_IO03
muxctrl_reg64 0x1f207d1c 0x24 PAD_SR_IO04
muxctrl_reg65 0x1f207d20 0x24 PAD_SR_IO05
muxctrl_reg66 0x1f207d24 0x24 PAD_SR_IO06
muxctrl_reg67 0x1f207d28 0x24 PAD_SR_IO07
muxctrl_reg68 0x1f207d2c 0x14 PAD_SR_IO08
muxctrl_reg69 0x1f207d30 0x14 PAD_SR_IO09
muxctrl_reg70 0x1f207d34 0x14 PAD_SR_IO10
muxctrl_reg71 0x1f207d38 0x14 PAD_SR_IO11
muxctrl_reg72 0x1f207d3c 0x254 PAD_SR_IO12
muxctrl_reg73 0x1f207d40 0x254 PAD_SR_IO13
muxctrl_reg74 0x1f207d44 0x254 PAD_SR_IO14
muxctrl_reg75 0x1f207d48 0x25b PAD_SR_IO15
muxctrl_reg76 0x1f207d4c 0x255 PAD_SR_IO16
muxctrl_reg77 0x1f207d50 0x255 PAD_SR_IO17
muxctrl_reg78 0x1f207d54 0x255 PAD_SAR_GPIO3
muxctrl_reg79 0x1f207d58 0x255 PAD_SAR_GPIO2
muxctrl_reg80 0x1f207d5c 0x255 PAD_SAR_GPIO1
muxctrl_reg81 0x1f207d60 0x255 PAD_SAR_GPIO0
```

```
IPL g2472466
D-00
HW Reset
miupll_200MHz
64MB
BIST0_0001-OK
RDQS cali
WDQS cali
SPI 54M

IPL_CUST g2472466
Version: I6C#gfdd7c70
DRAM:  
WARNING: Caches not enabled
Flash: [FLASH] find u32_sni_address = 0x9000
[FLASH] Device id is 0x20 0x40 0x18
[FLASH] SNI match flash.
[SPINOR] ReadData = 0x6b
[SPINOR] Dummy = 0x8
[SPINOR] pageProgram = 0x2
[FLASH] BDMA mode
[SPINOR] complement = 0x0
[SPINOR] top/buttom = 0x0
[SPINOR] blocks = 0x0
[SPINOR] SRP0 = 0x0
[SPINOR] SRP1 = 0x0
[FLASH] End flash init.
flash init successful
[PARTS] Load parts tbl from 0xa000
[PARTS] Got PNI @ 0x239ff040
mtd .name = nor0, .size = 0x01000000 (16MiB) .erasesize = 0x00001000 .numeraseregions = 0
SF: add mtd device successfully
SF: Detected nor0 with total size 16 MiB
16 MiB
*** Warning - bad CRC, using default environment

In:    serial
Out:   serial
Err:   serial
ir-cut gpio init
gpio[81] is 1
gpio[81] is 0
green led gpio init
gpio[11] is 0
red led gpio init
gpio[10] is 1
Net:   skip eth init
Autobooting in 1 seconds
Firmware check pass!
IMG_RADIO_LEN defined, RADIO_LEN = 0x10000
device 533070467 offset 0x60000, size 0x10000
SF: 65536 bytes @ 0x60000 Read: OK (cost 6 ms)
[XZ] !!!reserved 0x21000000 length=0x 1000000 for xz!!
XZ params: in_addr 0x21000040, in_size 0x10000, out_addr 0x220a0000, out_size 0x40000
XZ: uncompress ret 7, size = 262144
�Version: I6C#gfdd7c70n at 0x220A0000 ...
DRAM:  
WARNING: Caches not enabled
Flash: [FLASH] find u32_sni_address = 0x9000
[FLASH] Device id is 0x20 0x40 0x18
[FLASH] SNI match flash.
[SPINOR] ReadData = 0x6b
[SPINOR] Dummy = 0x8
[SPINOR] pageProgram = 0x2
[FLASH] BDMA mode
[SPINOR] complement = 0x0
[SPINOR] top/buttom = 0x0
[SPINOR] blocks = 0x0
[SPINOR] SRP0 = 0x0
[SPINOR] SRP1 = 0x0
[FLASH] End flash init.
flash init successful
[PARTS] Load parts tbl from 0xa000
[PARTS] Got PNI @ 0x21c9f040
mtd .name = nor0, .size = 0x01000000 (16MiB) .erasesize = 0x00001000 .numeraseregions = 0
SF: add mtd device successfully
SF: Detected nor0 with total size 16 MiB
16 MiB
*** Warning - bad CRC, using default environment

In:    serial
Out:   serial
Err:   serial
ir-cut gpio init
gpio[81] is 1
gpio[81] is 0
green led gpio init
gpio[11] is 0
red led gpio init
gpio[10] is 1
VF: validateFirmwareWithRecover: copying flash to 0x22100000
device 65536 whole chip
SF: 16777216 bytes @ 0x0 Read: OK (cost 697 ms)
VF: validateFirmwareWithRecover: ret=0(21c9ddcc)
VF: validateFirmwareWithRecover: validate local firmware...
TP Header at 22170000
device -1344052619 offset 0x70000, size 0x300000
SF: 3145728 bytes @ 0x70000 Read: OK (cost 131 ms)
##  Booting kernel from Legacy Image at 23000200 ...
   Image Name:   MVX4##I6C#gfdd7c70KL_LX510##[BR:
   Image Type:   ARM Linux Kernel Image (lzma compressed)
   Data Size:    1792380 Bytes = 1.7 MiB
   Load Address: 20008000
   Entry Point:  20008000
   Verifying Checksum ... OK
   Uncompressing Kernel Image ... 
[XZ] !!!reserved 0x21000000 length=0x 1000000 for xz!!
   XZ: uncompressed size=0x37f820, ret=7
OK
atags:0x20000000

Starting kernel ...

[    0.000000] Booting Linux on physical CPU 0x0
[    0.000000] Linux version 5.10.61 (root@smartlifeci1) (arm-linux-uclibcgnueabihf-9.1.0-gcc (crosstool-NG 1.24.0) 9.1.0, GNU ld (crosstool-NG 1.24.0) 2.32) #9 PREEMPT Thu May 16 19:02:484
[    0.000000] CPU: ARMv7 Processor [411fd040] revision 0 (ARMv7), cr=50c5383d
[    0.000000] CPU: div instructions available: patching division code
[    0.000000] CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
[    0.000000] early_atags_to_fdt() success
[    0.000000] OF: fdt: Machine model: INFINITY6C SSC027A-S01A
[    0.000000] LXmem is 0x4000000 PHYS_OFFSET is 0x20000000
[    0.000000] Add mem start 0x20000000 size 0x4000000!!!!
[    0.000000] 
[    0.000000] LX_MEM  = 0x20000000, 0x4000000
[    0.000000] LX_MEM2 = 0x0, 0x0
[    0.000000] LX_MEM3 = 0x0, 0x0
[    0.000000] MMU_MEM = 0x0, 0x0
[    0.000000] EMAC_LEN= 0x0
[    0.000000] DRAM_LEN= 0x0
[    0.000000] Memory policy: Data cache writeback
[    0.000000] Reserved memory: bypass cma0 node, using cmdline CMA params instead
[    0.000000] OF: reserved mem: node cma0 compatible matching fail
[    0.000000] no any mmap reserved
[    0.000000] deal_with_reserve_mma_heap memblock_reserve success mma_config[0].reserved_start=
[    0.000000] 0x22500000
[    0.000000] 
[    0.000000] cma: Reserved 2 MiB at 0x22200000
[    0.000000] Zone ranges:
[    0.000000]   Normal   [mem 0x0000000020000000-0x00000000224fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000020000000-0x00000000224fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000020000000-0x00000000224fffff]
[    0.000000] CPU: All CPU(s) started in SVC mode.
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 9398
[    0.000000] Kernel command line: WBWA root=/dev/mtdblock6 rootfstype=squashfs ro spdev=/dev/mtdblock7 init=/etc/preinit LX_MEM=0x4000000 mma_heap=mma_heap_name0,miu=0,sz=0x1b00000 mma_mM
[    0.000000] Dentry cache hash table entries: 8192 (order: 3, 32768 bytes, linear)
[    0.000000] Inode-cache hash table entries: 4096 (order: 2, 16384 bytes, linear)
[    0.000000] mem auto-init: stack:off, heap alloc:off, heap free:off
[    0.000000] Memory: 31592K/37888K available (2301K kernel code, 350K rwdata, 664K rodata, 108K init, 115K bss, 4248K reserved, 2048K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] rcu: Preemptible hierarchical RCU implementation.
[    0.000000]  Trampoline variant of Tasks RCU enabled.
[    0.000000] rcu: RCU calculated value of scheduler-enlistment delay is 10 jiffies.
[    0.000000] NR_IRQS: 16, nr_irqs: 16, preallocated irqs: 16
[    0.000000] GICv3: 192 SPIs implemented
[    0.000000] GICv3: 0 Extended SPIs implemented
[    0.000000] GICv3: Distributor has no Range Selector support
[    0.000000] GICv3: 16 PPIs implemented
[    0.000000] GICv3: CPU0: found redistributor 0 region 0:0x16040000
[    0.000000] ms_init_main_intc: np->name=ms_main_intc, parent=gic
[    0.000000] ms_init_pm_intc: np->name=ms_pm_intc, parent=ms_main_intc
[    0.000000] ss_init_gpi_intc: np->name=ms_gpi_intc, parent=ms_main_intc
[    0.000000] random: get_random_bytes called from 0xc03157fd with crng_init=0
[    0.000000] Find CLK_cpupll_clk, hook ms_cpuclk_ops
[    0.000000] arch_timer: cp15 timer(s) running at 6.00MHz (virt).
[    0.000000] clocksource: arch_sys_counter: mask: 0xffffffffffffff max_cycles: 0x1623fa770, max_idle_ns: 440795202238 ns
[    0.000007] sched_clock: 56 bits at 6MHz, resolution 166ns, wraps every 4398046511055ns
[    0.000024] Switching to timer-based delay loop, resolution 166ns
[    0.328071] printk: console [ttyS0] enabled
[    0.332261] Calibrating delay loop (skipped), value calculated using timer frequency.. 12.00 BogoMIPS (lpj=60000)
[    0.342520] pid_max: default: 4096 minimum: 301
[    0.347187] Mount-cache hash table entries: 1024 (order: 0, 4096 bytes, linear)
[    0.354366] Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes, linear)
[    0.362669] CPU: Testing write buffer coherency: ok
[    0.367571] Setting up static identity map for 0x200081c0 - 0x200081f8
[    0.373566] rcu: Hierarchical SRCU implementation.
[    0.378820] devtmpfs: initialized
[    0.382289] VFP support v0.3: implementor 41 architecture 3 part 40 variant 4 rev 3
[    0.389471] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
[    0.399095] futex hash table entries: 16 (order: -4, 448 bytes, linear)
[    0.406722] NET: Registered protocol family 16
[    0.411680] DMA: preallocated 256 KiB pool for atomic coherent allocations
[    0.418719] 
[    0.418719] 
[    0.418719] Version : MVX4##I6C#gfdd7c70KL_LX510##[BR:HEAD]#XVM
[    0.418719] 
[    0.459562] GPIO: probe end
[    0.472248] usbcore: registered new interface driver usbfs
[    0.479732] usbcore: registered new interface driver hub
[    0.483276] usbcore: registered new device driver usb
[    0.491263] clocksource: Switched to clocksource arch_sys_counter
[    0.496634] NET: Registered protocol family 2
[    0.500399] IP idents hash table entries: 2048 (order: 2, 16384 bytes, linear)
[    0.506855] tcp_listen_portaddr_hash hash table entries: 256 (order: 0, 6144 bytes, linear)
[    0.514660] TCP established hash table entries: 1024 (order: 0, 4096 bytes, linear)
[    0.522160] TCP bind hash table entries: 1024 (order: 2, 20480 bytes, linear)
[    0.529272] TCP: Hash tables configured (established 1024 bind 1024)
[    0.535771] UDP hash table entries: 128 (order: 0, 6144 bytes, linear)
[    0.542174] UDP-Lite hash table entries: 128 (order: 0, 6144 bytes, linear)
[    0.549239] NET: Registered protocol family 1
[    0.556083] Initialise system trusted keyrings
[    0.558768] workingset: timestamp_bits=30 max_order=14 bucket_order=0
[    0.564532] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.570160] jffs2: version 2.2. © 2001-2006 Red Hat, Inc.
[    0.575921] Key type asymmetric registered
[    0.579722] Asymmetric key parser 'x509' registered
[    0.584726] io scheduler mq-deadline registered
[    0.590799] zram: Added device: zram0
[    0.594795] libphy: Fixed MDIO Bus: probed
[    0.596870] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.604029] Sstar_ehc_init version:20180309
[    0.608032] i2c /dev entries driver
[    0.612543] MSYS: DMEM request: [Sstar URDMA 0 TX]:0x00001000
[    0.612551] MSYS: DMEM request alignment: [Sstar URDMA 0 TX]:0x00002000
[    0.612677] MSYS: DMEM request: [Sstar URDMA 0 TX]:0x00002000 success, CPU phy:@0x0000000022240000, virt:@(ptrval)
[    0.612685] MSYS: DMEM request: [Sstar URDMA 0 RX]:0x00001000
[    0.612690] MSYS: DMEM request alignment: [Sstar URDMA 0 RX]:0x00002000
[    0.612733] MSYS: DMEM request: [Sstar URDMA 0 RX]:0x00002000 success, CPU phy:@0x0000000022242000, virt:@(ptrval)
[    0.656530] 1f221000.uart0: ttyS0 at MMIO 0x0 (irq = 35, base_baud = 10750000) is a unknown
[    0.665371] MSYS: DMEM request: [Sstar URDMA 1 TX]:0x00001000
[    0.670590] MSYS: DMEM request alignment: [Sstar URDMA 1 TX]:0x00002000
[    0.677691] MSYS: DMEM request: [Sstar URDMA 1 TX]:0x00002000 success, CPU phy:@0x0000000022244000, virt:@(ptrval)
[    0.687614] MSYS: DMEM request: [Sstar URDMA 1 RX]:0x00001000
[    0.693344] MSYS: DMEM request alignment: [Sstar URDMA 1 RX]:0x00002000
[    0.699962] MSYS: DMEM request: [Sstar URDMA 1 RX]:0x00002000 success, CPU phy:@0x0000000022246000, virt:@(ptrval)
[    0.710343] 1f221200.uart1: ttyS1 at MMIO 0x0 (irq = 38, base_baud = 10750000) is a unknown
[    0.719155] MSYS: DMEM request: [Sstar URDMA 2 TX]:0x00001000
[    0.724787] MSYS: DMEM request alignment: [Sstar URDMA 2 TX]:0x00002000
[    0.731066] MSYS: DMEM request: [Sstar URDMA 2 TX]:0x00002000 success, CPU phy:@0x0000000022248000, virt:@(ptrval)
[    0.741423] MSYS: DMEM request: [Sstar URDMA 2 RX]:0x00001000
[    0.747094] MSYS: DMEM request alignment: [Sstar URDMA 2 RX]:0x00002000
[    0.753777] MSYS: DMEM request: [Sstar URDMA 2 RX]:0x00002000 success, CPU phy:@0x000000002224A000, virt:@(ptrval)
[    0.764119] 1f220400.fuart: ttyS2 at MMIO 0x0 (irq = 41, base_baud = 10750000) is a unknown
[    0.773403] [ss_gpi_intc_domain_alloc] hw:31 -> v:77
[    0.778848] >> [sdmmc] ms_sdmmc_probe 
[    0.781128] Fail to get pad(131075) form padmux !
[    0.786448] Fail to get pad(0) form padmux !
[    0.790219] [ss_gpi_intc_domain_alloc] hw:22 -> v:78
[    0.795518] >> [sdmmc_0] Probe Platform Devices
[    0.800504] MSYS: DMEM request: [emac0_buff]:0x00000212
[    0.805419] MSYS: DMEM request alignment: [emac0_buff]:0x00002000
[    0.810966] MSYS: DMEM request: [emac0_buff]:0x00002000 success, CPU phy:@0x000000002224E000, virt:@(ptrval)
[    0.821798] libphy: mdio: probed
[    0.823953] mdio_bus mdio-bus@emac0: ethernet-phy@0 has invalid PHY address
[    0.830916] mdio_bus mdio-bus@emac0: scan phy ethernet-phy at address 0
[    0.838631] [emac_phy_connect][3794] connected mac emac0 to PHY at mdio-bus@emac0:00 [uid=11112222, driver=SStar 10/100 Ethernet Phy]
[    0.858130] MSYS: DMEM request: [AESDMA_ENG]:0x00001000
[    0.860511] MSYS: DMEM request alignment: [AESDMA_ENG]:0x00002000
[    0.867627] MSYS: DMEM request: [AESDMA_ENG]:0x00002000 success, CPU phy:@0x0000000022250000, virt:@(ptrval)
[    0.877080] MSYS: DMEM request: [AESDMA_ENG1]:0x00001000
[    0.881926] MSYS: DMEM request alignment: [AESDMA_ENG1]:0x00002000
[    0.888000] MSYS: DMEM request: [AESDMA_ENG1]:0x00002000 success, CPU phy:@0x0000000022252000, virt:@(ptrval)
[    0.898727] ms_cpufreq_init 433 SIDD: 0x130 OSC:0xea 
[    0.903479] ms_cpufreq_init 434 SIDD Thres: 0x113 OSC Thres:0xf0 
[    0.909252] [ms_cpufreq_init] Current clk=801358688
[    0.915014] read pad-ctrl failed
[    0.918075] [NOTICE]pwm-isr(68) success. If not i6e or i6b0, pls confirm it on .dtsi
[    0.925585] [MSPI] mspi 0 use dma mode
[    0.929748] [MSPI] mspi 1 use dma mode
[    0.935266] [FLASH] find u32_sni_address = 0x9000
[    0.938157] [FLASH] Device id is 0x20 0x40 0x18
[    0.943000] [FLASH] SNI match flash.
[    0.945611] [SPINOR] ReadData = 0x6b
[    0.949108] [SPINOR] Dummy = 0x8
[    0.952485] [SPINOR] pageProgram = 0x2
[    0.956245] [FLASH] BDMA mode
[    0.959305] [SPINOR] complement = 0x0
[    0.963085] [SPINOR] top/buttom = 0x0
[    0.966790] [SPINOR] blocks = 0x0
[    0.970184] [SPINOR] SRP0 = 0x0
[    0.973515] [SPINOR] SRP1 = 0x0
[    0.976612] [FLASH] End flash init.
[    0.980183] MSYS: DMEM request: [BDMA]:0x00010000
[    0.985057] MSYS: DMEM request: [BDMA]:0x00010000 success, CPU phy:@0x0000000022260000, virt:@(ptrval)
[    0.994258] _serflash_alloc_bdma_buffer _BDMA_ALLOC_DMEM.bdma_vir_addr 0xc2260000
[    0.994268] serflash_probe: 7mtd .name = nor0, .size = 0x01000000 (16MiB)
[    0.994268]  .erasesize = 0x00001000 .numeraseregions = 0
[    0.994268] 
[    1.015440] SLP flash nor read
[    1.018527] MTD_REDBOOT_TP_HEADER_ADDRESS:0x70000
[    1.028285] decrypt_rootfs_header done
[    1.029171] Searching for RedBoot partition table
[    1.033891] 16 RedBoot partitions found on MTD device nor0
[    1.039358] partitions[ 0] = {.offset = 0x00000000, .size = 0x00030000 (    192 KiB), .name = factory_boot  }
[    1.049287] partitions[ 1] = {.offset = 0x00030000, .size = 0x00010000 (     64 KiB), .name = factory_info  }
[    1.059217] partitions[ 2] = {.offset = 0x00040000, .size = 0x00010000 (     64 KiB), .name = art           }
[    1.069131] partitions[ 3] = {.offset = 0x00050000, .size = 0x00010000 (     64 KiB), .name = config        }
[    1.079052] partitions[ 4] = {.offset = 0x00060000, .size = 0x00010000 (     64 KiB), .name = normal_boot   }
[    1.088982] partitions[ 5] = {.offset = 0x00070200, .size = 0x001bfe00 (   1791 KiB), .name = kernel        }
[    1.098897] partitions[ 6] = {.offset = 0x00230000, .size = 0x001d0000 (   1856 KiB), .name = rootfs        }
[    1.108819] partitions[ 7] = {.offset = 0x00400000, .size = 0x00b70000 (  11712 KiB), .name = rootfs_data   }
[    1.118749] partitions[ 8] = {.offset = 0x00f70000, .size = 0x00080000 (    512 KiB), .name = user_record   }
[    1.128664] partitions[ 9] = {.offset = 0x00ff0000, .size = 0x00010000 (     64 KiB), .name = verify        }
[    1.138586] partitions[10] = {.offset = 0x00070000, .size = 0x00f00000 (  15360 KiB), .name = firmware      }
[    1.148515] partitions[11] = {.offset = 0x00000000, .size = 0x00000000 (      0 KiB), .name = uitron        }
[    1.158430] partitions[12] = {.offset = 0x00000000, .size = 0x00000000 (      0 KiB), .name = uitron_ext    }
[    1.168352] partitions[13] = {.offset = 0x00000000, .size = 0x00000000 (      0 KiB), .name = ld            }
[    1.178281] partitions[14] = {.offset = 0x00000000, .size = 0x00000000 (      0 KiB), .name = isp           }
[    1.188197] partitions[15] = {.offset = 0x00040000, .size = 0x00000000 (      0 KiB), .name = af            }
[    1.198115] Mtd parts default
[    1.198120] Creating 16 MTD partitions on "nor0":
[    1.205787] 0x000000000000-0x000000030000 : "factory_boot"
[    1.222294] 0x000000030000-0x000000040000 : "factory_info"
[    1.232494] 0x000000040000-0x000000050000 : "art"
[    1.235811] 0x000000050000-0x000000060000 : "config"
[    1.252301] 0x000000060000-0x000000070000 : "normal_boot"
[    1.256290] 0x000000070200-0x000000230000 : "kernel"
[    1.272333] 0x000000230000-0x000000400000 : "rootfs"
[    1.275906] 0x000000400000-0x000000f70000 : "rootfs_data"
[    1.292299] 0x000000f70000-0x000000ff0000 : "user_record"
[    1.296350] 0x000000ff0000-0x000001000000 : "verify"
[    1.312306] 0x000000070000-0x000000f70000 : "firmware"
[    1.316062] 0x000000000000-0x000001000000 : "uitron"
[    1.332422] 0x000000000000-0x000001000000 : "uitron_ext"
[    1.336337] 0x000000000000-0x000001000000 : "ld"
[    1.352306] 0x000000000000-0x000001000000 : "isp"
[    1.355607] 0x000000040000-0x000001000000 : "af"
[    1.372739] sstar-u2phy soc:sstar-usb2-phy: No extra phy data
[    1.376145] NET: Registered protocol family 17
[    1.380309] Loading compiled-in X.509 certificates
[    1.386214] Sstar-ehci 1f284800.Sstar-ehci-1: [USB] no platform_data, device tree coming
[    1.393052] Sstar-ehci 1f284800.Sstar-ehci-1: [USB][EHC] dma coherent_mask 0xffffffff mask 0xffffffff
[    1.402368] [USB] config miu select [70] [e8] [ef] [ef]
[    1.407407] [USB] enable miu lower bound address subtraction
[    1.413090] Sstar-ehci 1f284800.Sstar-ehci-1: [USB] hcd ehc:fd284800 usbc:c081b200 bc:c081b000
[    1.421717] Sstar-ehci 1f284800.Sstar-ehci-1: [USB] 1f284800.Sstar-ehci-1 irq --> 74
[    1.429614] phy phy-soc:sstar-usb2-phy.0: squelch level 0x00000002
[    1.436879] phy phy-soc:sstar-usb2-phy.0: DP/DM no swap
[    1.440826] phy phy-soc:sstar-usb2-phy.0: sstar_u2phy_utmi_init
[    1.446802] phy phy-soc:sstar-usb2-phy.0: Set phy mode -> host
[    1.452608] phy phy-soc:sstar-usb2-phy.0: Default UTMI eye diagram parameter setting
[    1.460325] phy phy-soc:sstar-usb2-phy.0: sstar_u2phy_utmi_power_on
[    1.466616] Sstar-ehci 1f284800.Sstar-ehci-1: EHCI Host Controller
[    1.472809] Sstar-ehci 1f284800.Sstar-ehci-1: new USB bus registered, assigned bus number 1
[    1.481285] phy phy-soc:sstar-usb2-phy.0: Init UTMI disconnect level setting
[    1.488297] Sstar-ehci 1f284800.Sstar-ehci-1: irq 74, io mem 0x1f284800
[    1.521370] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.10
[    1.526789] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.534185] usb usb1: Product: EHCI Host Controller
[    1.538887] usb usb1: Manufacturer: Linux 5.10.61 ehci_hcd
[    1.544382] usb usb1: SerialNumber: sstar
[    1.549014] hub 1-0:1.0: USB hub found
[    1.552701] hub 1-0:1.0: 1 port detected
[    1.556402] Sstar-ehci 1f284800.Sstar-ehci-1: ehci_hcd_sstar_usbc_settings
[    1.563643] OF: fdt: not creating '/sys/firmware/fdt': CRC check failed
[    1.570051] Registered character driver slp_flash_chrdev
[    1.575071] SLP flash cdev init!  nor0
[    1.575096] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    1.589013] cfg80211: Problem loading in-kernel X.509 certificate (-129)
[    1.593280] platform regulatory.0: Direct firmware load for regula[    1.604540] VFS: Mounted root (squashfs filesystem) readonly on device 31:6.
[    1.606244] devtmpfs: mounted
[    1.606309] Kernel memory protection not selected by kernel config.
[    1.606392] Run /etc/preinit as init process
[    1.611283] The number of fuart send must more than 1 Byte!
[    1.624741] cfg80211: failed to load regulatory.db
[    1.639265] process '/bin/busybox' started with executable stack
[    1.700725] random: preinit: uninitialized urandom read (4 bytes read)
[    1.778215] random: busybox: uninitialized urandom read (4 bytes read)
[    1.780757] random: busybox: uninitialized urandom read (4 bytes read)
[    1.821385] usb usb1-port1: hub_port_connect: add adjust_async_ladr flag
[    2.011322] usb 1-1: new high-speed USB device number 2 using Sstar-ehci
[    2.011435] Sstar-ehci 1f284800.Sstar-ehci-1: [switch] reg is 0x224d000, 0x10001, 0xd
[    2.252457] usb 1-1: New USB device found, idVendor=0bda, idProduct=f179, bcdDevice= 0.00
[    2.252582] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.252682] usb 1-1: SerialNumber: B01921E70D1B
[    2.253521] phy phy-soc:sstar-usb2-phy.0: high-speed connect
[    2.687882] overlayfs: upper fs does not support tmpfile.
[    2.687983] overlayfs: upper fs does not support RENAME_WHITEOUT.
[    2.688052] overlayfs: upper fs does not support xattr, falling back to index=off and metacopy=off.

Please press Enter to activate this console. [    2.730591] zram0: detected capacity change from 0 to 16777216
Setting up swapspace version 1, size = 16773120 bytes
UUID=5733f685-21e0-4755-a49a-40161226bfce
[    2.751511] Adding 16380k swap on /dev/zram0.  Priority:-2 extents:1 across:16380k SS
[    2.788816] kdms: loading out-of-tree module taints kernel.
[    2.789228] error:sock_send_netlink return < 0 | error
[    2.789298] error:sock_send_netlink return < 0 | error
Monitor: create event handler ok.

 log err size:65536.
[1970-01-01 08:00:03] [ERROR] preinit_main():512 - [NVMP]Fail to register final_stage
base-files/
base-files/etc/
base-files/etc/isp.config
base-files/etc/oem.config
base-files/etc/system.config
base-files/etc/encrypt_key
base-files/etc/ams.config
base-files/etc/module_spec.config
base-files/etc/audio.config
base-files/cfg/
base-files/cfg/isp_night_wl.bin
base-files/cfg/isp_day.bin
base-files/cfg/isp_night.bin
base-files/cfg/isp_night_near.bin
radio/
radio/PHY_REG_PG.txt
radio/.gitkeep
radio/8188FTV_mask.txt
radio/wifi_efuse_8188fu.map
[    4.318586] mhal module [vcodec] init
[    4.318929] [ven-m][sys] DrvVencProbe:228 vcodec prob sucess.
[    4.319603] [ven-m][jpeg] jpe driver probed
[    4.319803] mhal module [aio] init
[    4.319869] module [sys] init May 13 2024 18:10:19
[    4.320214] start:0x20000000,end:0x24000000,block_id:0,flag:1
[    4.320282] HAL_MIU_Protect 791 start=20000000, 24000000 u8Blockx=0
[    4.320851] start:0x20000000,end:0x24000000,block_id:0,flag:0
[    4.320924] HAL_MIU_Protect 791 start=20000000, 24000000 u8Blockx=0
[    4.321007] start:0x20000000,end:0x22500000,block_id:0,flag:1
[    4.321071] HAL_MIU_Protect 791 start=20000000, 22500000 u8Blockx=0
[    4.321168] mi_sys_mma_allocator_create success, heap_base_addr=20000000 length=3a800 
[    4.321767] mhal module [vif] init
[    4.322276] g_stSelSpinLock init.
[    4.322751] module [vif] init
[    4.322888] mhal module [sensor] init
[    4.323953] module [sensor] init
[    4.324139] mhal module [rgn] init
[    4.324409] module [rgn] init
[    4.324588] module [ao] init
[    4.324718] module [ai] init
[    4.324858] mhal module [isp] init
[    4.326467]  ~~~~~~~~~~~ Mload Inside init module ~~~~~~~~~~~~~~~
[    4.326660] module [isp] init
[    4.327112] module [ipu] init
[    4.327286] mhal module [vpe] init
[    4.327665] module [scl] init
[    4.327848] module [venc] init May 13 2024 18:10:18
[    4.327997] mhal module [ldc] init
[    4.328114] module [ldc] init
BANK:0x1038 16bit-offset 0x01
0x0004
BANK:0x1038 16bit-offset 0x01
0x001C
BANK:0x1038 16bit-offset 0x01
0x003C
BANK:0x1038 16bit-offset 0x61
0x1014
[    4.359962] srcfg driver 1.0 register success!

detecting sensor sc3235_MIPI...
[    4.417314] g_stSelSpinLock init.
[    4.417399] 
[    4.417399] Sensor configuration, ID=0, Bus=2, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    4.417399] 
[    4.450961] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
[    4.468303] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
detect sensor sc3235_MIPI result: 0

detecting sensor SC200ai_MIPI...
[    4.531885] g_stSelSpinLock init.
[    4.531970] 
[    4.531970] Sensor configuration, ID=0, Bus=2, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    4.531970] 
[    4.563377] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
[    4.580832] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
detect sensor SC200ai_MIPI result: 0

detecting sensor SC500ai_MIPI...
[    4.644989] g_stSelSpinLock init.
[    4.645074] 
[    4.645074] Sensor configuration, ID=0, Bus=2, Lane=1, MCLK=27000, PWD_PIN=0, RST_PIN=1 
[    4.645074] 
[    4.677065] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
[    4.694947] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
detect sensor SC500ai_MIPI result: 0

detecting sensor sc8235_MIPI...
[    4.760531] g_stSelSpinLock init.
[    4.760615] 
[    4.760615] Sensor configuration, ID=0, Bus=3, Lane=1, MCLK=27000, PWD_PIN=0, RST_PIN=1 
[    4.760615] 
[    4.793325] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
[    4.811224] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
detect sensor sc8235_MIPI result: 0

detecting sensor gc4653_MIPI...
[    4.879704] g_stSelSpinLock init.
[    4.879789] 
[    4.879789] Sensor configuration, ID=0, Bus=2, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    4.879789] 
[    4.912997] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
[    4.934591] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
detect sensor gc4653_MIPI result: 0

detecting sensor sc3335_MIPI...
[    5.000078] g_stSelSpinLock init.
[    5.000162] 
[    5.000162] Sensor configuration, ID=0, Bus=2, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    5.000162] 
[    5.037130] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
[    5.055601] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
detect sensor sc3335_MIPI result: 0

detecting sensor sc530ai_MIPI...
[    5.125452] g_stSelSpinLock init.
[    5.125537] 
[    5.125537] Sensor configuration, ID=0, Bus=2, Lane=1, MCLK=27000, PWD_PIN=0, RST_PIN=1 
[    5.125537] 
[    5.159836] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
[    5.178591] err:i2c-1 xfer error: -7
Read RegisterPair set register: Operation not permitted
detect sensor sc530ai_MIPI result: 0

detecting sensor sc5239_MIPI...
[    5.249716] g_stSelSpinLock init.
[    5.249812] 
[    5.249812] Sensor configuration, ID=0, Bus=1, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    5.249812] 
detect sensor sc5239_MIPI result: 0

detecting sensor SC401AI_MIPI...
[    5.362612] g_stSelSpinLock init.
[    5.362707] 
[    5.362707] Sensor configuration, ID=0, Bus=1, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    5.362707] 
detect sensor SC401AI_MIPI result: 0

detecting sensor sc4336p_MIPI...
[    5.477891] g_stSelSpinLock init.
[    5.477986] 
[    5.477986] Sensor configuration, ID=0, Bus=1, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    5.477986] 
detect sensor sc4336p_MIPI result: 0

detecting sensor sc4336_MIPI...
[    5.595278] g_stSelSpinLock init.
[    5.595373] 
[    5.595373] Sensor configuration, ID=0, Bus=1, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    5.595373] 
detect sensor sc4336_MIPI result: 0

detecting sensor sc430ai_MIPI...
[    5.715417] g_stSelSpinLock init.
[    5.715511] 
[    5.715511] Sensor configuration, ID=0, Bus=1, Lane=1, MCLK=27000, PWD_PIN=1, RST_PIN=1 
[    5.715511] 
detect sensor sc430ai_MIPI result: 1
sensor_name=sc430ai_MIPI
========== Sensor sc430ai_MIPI was detected! =============
insmod /config/auto_detect_sensor/modules/sc430ai_MIPI.ko chmap=1
[1970-01-01 08:00:05] mb_main():769 - [MB]mb mb_main.
[1970-01-01 08:00:05] nvmp_print_start():300 - [NVMP]Main progress start ...
Monitor: receive NVMP_START. (uptime:6)
[1970-01-01 08:00:05] [ERROR] load_config_file():210 - [NVMP]ds_to_multi_bin failed, module_name=md_pir
[1970-01-01 08:00:05] [ERROR] load_config_file():210 - [NVMP]ds_to_multi_bin failed, module_name=uhttpd
[    6.159110] gpio_params_init()-988 LED_1_GPIO[10] LED_2_GPIO[11] LED_3_GPIO[0] LED_4_GPIO[0] 
[    6.159292] init_gpio_pins()-1097 default on s_gpio[10] 
[2024-05-16 19:05:10] sntpc_init():650 - [SNTPC]Init over
[2024-05-16 19:05:10] tpntp_init():589 - [TPNTP]Init over
[2024-05-16 19:05:10] ntp_time_update_cb():637 - [SYSTEM]System time is calibrated by FW build time.
[2024-05-16 19:05:10] [ERROR] factory_info_init():2827 - [TMPD]isp version read is 1
[    6.231830] [emac_phy_link_adjust] EMAC Link Down 
[2024-05-16 19:05:10] nifc_init():1349 - [NIFC]Interface eth0 up
[2024-05-16 19:05:10] nifc_init():1359 - [NIFC]Interface lo up
[2024-05-16 19:05:10] nifc_init():1387 - [NIFC]Interface br-wan up
[2024-05-16 19:05:10] [ERROR] dhcpc_socket_raw_init():1256 - [DHCPC]Got raw socket fd 8
[2024-05-16 19:05:10] dhcpc_socket_raw_init():1316 - [DHCPC]Attached filter to raw socket fd 8
[2024-05-16 19:05:10] [ERROR] dhcpc_socket_raw_init():1327 - [DHCPC]Created raw socket
[2024-05-16 19:05:10] [ERROR] dhcpc_init():1457 - [DHCPC]DHCPC init over.
[2024-05-16 19:05:10] osd_init():2487 - [OSD]Osd init success.
[INFO]:ST_Sys_Init[36]: 
u8Version:Sigmastar Module version: project_commit.1cc8df8 sdk_commit.e50e9b2 mhal_commit.2f13353 build_time.20240513181014
[INFO]:ST_Sys_Init[39]: 
u64Pts:0x5dece8
[DBG]:ST_Common_SensorInit[188]: index 0, Crop(0,0,2688,1520), outputsize(2688,1520), maxfps 30, minfps 3, ResDesc 2688x1520@30fps
[DBG]:ST_Common_SensorInit[188]: index 1, Crop(64,40,2560,1440), outputsize(2688,1520), maxfps 30, minfps 3, ResDesc 2560x1440@30fps
[DBG]:ST_Common_SensorInit[188]: index 2, Crop(0,0,2688,1520), outputsize(2688,1520), maxfps 60, minfps 3, ResDesc 2688x1520@60fps
[DBG]:ST_Common_SensorInit[200]: resolution you need:0
[    6.321417] vif chipidx 9, version 1 
[DBG]:ST_Common_VifEnable[291]: set vif dev attr (0,0,2688,1520) 
[    6.322300] chipidx 9, revision 1 
[    6.322447] setbw level1 
[    6.324942] chn0, sub channel num 0 
[    6.325025] isp chn0, multi channel num 1 
[MI_ISP_CUS3A_Enable] AE = 1, AWB = 1, AF = 1
[MI_ISP_CUS3A_Enable] AE = 1, AWB = 1, AF = 1
[MI_ISP_CUS3A_Enable] AE = 1, AWB = 1, AF = 1
[    6.326026] chipidx 9, revision 1 
[    7.793329] [ss_gpi_intc_domain_alloc] hw:50 -> v:79
[2024-05-16 19:05:11] [ERROR] avts_init():3211 - [AVDM][AVTS]AVTS init over
[2024-05-16 19:05:11] [ERROR] http_auth_init():1560 - [HTTPD]ds_register_action of p2psharepwd.
[2024-05-16 19:05:11] [ERROR] ds_register_get_json():530 - [DS]Section wan get_json is set already.
[2024-05-16 19:05:11] [ERROR] init_special_url_map_list_head():773 - [HTTPD]list_head has been initialized
[2024-05-16 19:05:11] cover_init():726 - [COVER]Cover init over.
[2024-05-16 19:05:11] image_init():1401 - [IMAGE]Image init over.
[2024-05-16 19:05:11] record_plan_init():234 - [RECORD_PLAN]init over, ret[0]
[2024-05-16 19:05:11] msg_alarm_init():1776 - [MSG_ALARM]msg alarm init over.
[2024-05-16 19:05:11] hsr_alarm_init():1174 - [HSR]hsr_alarm init over.
[2024-05-16 19:05:11] vd_alarm_init():1166 - [VD_ALARM]vd_alarm init over.
[2024-05-16 19:05:11] ptd_alarm_init():1170 - [PTD_ALARM]ptd_alarm init over.
[2024-05-16 19:05:11] bcd_alarm_init():688 - [BCD_ALARM]bcd_alarm init over.
[2024-05-16 19:05:11] bark_alarm_init():689 - [BARK_ALARM]bark_alarm init over.
[2024-05-16 19:05:11] meow_alarm_init():689 - [MEOW_ALARM]meow_alarm init over.
[2024-05-16 19:05:11] glass_alarm_init():689 - [GLASS_ALARM]glass_alarm init over.
[2024-05-16 19:05:11] md_alarm_init():1596 - [MD_ALARM]md alarm init over.
[2024-05-16 19:05:11] cd_alarm_init():1481 - [CD]cd_alarm init over.
[2024-05-16 19:05:11] onvif_init_supported_event_topic():361 - [ONVIF]supported event topic md(1)-od(1)-cd(1)-id(0)-pd(1)-smart_det(1)
[2024-05-16 19:05:11] [ERROR] dr_init():1420 - [DR]dr init over.
debug_tools_init()-68 - [DEBUG_TOOLS]debug_tools init over.
[2024-05-16 19:05:11] upnpc_init():1051 - [UPNPC]upnpc init over
[2024-05-16 19:05:11] bcd_init():930 - [BCD_ALARM]bcd init over.
[    7.894532] [PWM] sstar_pwm_config duty_ns=0, period_ns=50000
[    7.894657] reg=0x1F203290 clk=12000000, period=0xef
[    7.894753] reg=x1F203288(x1019) clk=12000000, u32Duty=x0
[    7.895034] [PWM] sstar_pwm_config duty_ns=100, period_ns=50000
[    7.895154] reg=0x1F203290 clk=12000000, period=0xef
[    7.895250] reg=x1F203288(x1019) clk=12000000, u32Duty=xef
[2024-05-16 19:05:11] light_control_init():1085 - [MSG_ALARM]light control init over.
[2024-05-16 19:05:11] mb_init():762 - [MB]mb init over.
[    7.945496] slp_dev_ioctl()-620 only read uc2 offset:360448, len:32768
[2024-05-16 19:05:11] [ERROR] ds_load_usr_cfg():1812 - [DS]donnt need copy to UC[1]
[2024-05-16 19:05:11] [ERROR] set_auto_upgrade():526 - [SYSTEM]set_auto_upgrade 1 ...
[2024-05-16 19:05:11] [ERROR] set_auto_upgrade():586 - [SYSTEM]random seconds: 279s, upgrade_time: 1715886279
[2024-05-16 19:05:11] [ERROR] set_auto_upgrade_timer():489 - [SYSTEM]expire_seconds[28768]
[    7.950115] [ss_gpi_intc_domain_alloc] hw:9 -> v:80
[    7.950324] genirq: Setting trigger mode 3 for irq 80 failed (0xc018b67d)
[    7.950488] gpio not support irq
[2024-05-16 19:05:11] system_start():1964 - [SYSTEM]Start over
[2024-05-16 19:05:11] sntpc_start():764 - [SNTPC]sntpc_silent_retry_intvl : 30 s 
[2024-05-16 19:05:11] sntpc_start():799 - [SNTPC]Start over
[2024-05-16 19:05:11] nsd_start():443 - [NSD]Network services start ......
[2024-05-16 19:05:11] system_set_wan_rate():539 - [NIFC]wan_rate 0.
[2024-05-16 19:05:11] system_if_setup_speed_duplex():500 - [NIFC]Auto neg: Speed = 1000, full_duplex = 1
[2024-05-16 19:05:11] system_if_setup_speed_duplex():518 - [NIFC]ecmd: speed = 1000, duplex = 1, autoneg = 1.
[2024-05-16 19:05:11] [ERROR] system_if_del_gateway_route():267 - [NIFC]Ioctl SIOCDELRT error, ret code is -1, dst = 00000000, gateway = 0100a8c0.
[2024-05-16 19:05:11] link_status_update():361 - [NIFC]Link status: LINK_DOWN -> LINK_DOWN
[2024-05-16 19:05:11] link_status_update():362 - [NIFC]IP: *********, mask: 255.255.255.0, gateway: 192.168.0.1, DNS: 8.8.8.8, 8.8.4.4
[2024-05-16 19:05:11] nifc_start():1771 - [NIFC]Start over
[2024-05-16 19:05:11] dhcpc_start():1502 - [DHCPC]DHCPC start over.
[2024-05-16 11:05:11] [ERROR][CloudIot]cloud_iot.c:166(mqtt_timer_handler) - not authentication, request for auth key...

[2024-05-16 11:05:11] wlan_start():428 - [WLAN]WLAN start ......
[2024-05-16 11:05:11] __video_stream_init():2483 - strm_id init:0, framerate:20, bitrate:2048,u32CapWidth:2560,u32CapHeight:1440
[    7.969941] Create mi dev0 dev_type0
[    7.973658] Create mi dev0 dev_type1
[    7.973743] Create mhal dev0 dev_type0
[    7.973828] dev0 dev_type0 config memory base address:0x40000000
[    7.973997] [ven-m][vcodec] vcodec miu protect channel:venc:2 vdec:0
[    7.974176] heap_name mma_heap_codec  bEnable=1 
[    7.974273] au16SetProId[0]:0xc
[    7.974338] au16SetProId[1]:0x70
[    7.974408] miu_number:0,start:0x60064000,end:0x60128000,block_id:16,flag:1
[    7.974548] HAL_MIU_Protect 791 start=60064000, 60128000 u8Blockx=10
sh: write error: Invalid argument
[    8.023318] [ss_gpi_intc_domain_alloc] hw:8 -> v:81
[is_cal] wlan-manager: driver is not ready, wait...
[    8.080770] CmdqProcInit 1280
[    8.081236] CMDQ - IRQ Request 0 
[    8.081525] dev0 dev_type0 bAllowPreemptionSram:0 bNeedSram:1 bUsePreDevBuf:0 u32SramSize:18400
[    8.081692] Create mhal dev0 dev_type1
[    8.081771] dev0 dev_type1 bAllowPreemptionSram:0 bNeedSram:1 bUsePreDevBuf:0 u32SramSize:18400

src(6-0-0-0)  dst(33-0-0-0)  4...


src(33-0-0-0)  dst(34-0-0-0)  4...


src(34-0-0-0)  dst(2-0-0-0)  16...

[    8.191928] CMDQ - IRQ Request 1 
[    8.192109] MI WRN[ 166]output port0,set size(0,0,0,0), no support crop, adjust rect(0,0,2688,1520)
[    8.219451] CMDQ - IRQ Request 2 
[    AeInit] FPS (Init, Input, Output, Cur, Deband) = (   30,   30,   30,   30,   30)
[    AeInit] Use AE Short Histogram = Valid
[    AeInit] --> Change  :      1,    CurYx10 :      0, CurY1x10 :      0   , Targetx10 :    470, BVx16384 :  20765, FNx10 :  16, IspGain :   1024, SensorGain :   1024, Shutter  :  33232 us

[2024-05-16 11:05:12] __video_stream_init():2483 - strm_id init:1, framerate:20, bitrate:384,u32CapWidth:640,u32CapHeight:360
[      DoAe] FPS (Input, Output, Cur, Deband) = (   30,   30,30000,   30)
[AF_InitParameters-1932] Error!! Initial motor parameters got from motor driver are unreasonable. 
[AF_InitParameters-1933] InitPos = 0, MinMotorPos = 0, MaxMotorPos = 0, MinMotorStep = 1, MaxMotorStep = 0 

src(2-0-0-0)  dst(2-0-1-0)  16...

[2024-05-16 11:05:12] [ERROR] audio_ai_init():793 - [MPP]audio_in inited!
[ALGO_MSG_MSG] Checking IC....
[ALGO_MSG_MSG] [ANR] ANR IC check pass. ver.2022.0609.0000
[ALGO_MSG_MSG] [ANR] FFT mode: floating point mode
[ALGO_MSG_MSG] [ANR] Point Number: 128
[ALGO_MSG_MSG] [ANR] Channel: 1
[ALGO_MSG_MSG] [ANR] Sample rate: 8000
[ALGO_MSG_MSG] |--------------------------------------------------------------------------------|
[ALGO_MSG_MSG] |                                                                                |
[ALGO_MSG_MSG] |                                   NEON ENABLE                                  |
[ALGO_MSG_MSG] |                                                                                |
[ALGO_MSG_MSG] |--------------------------------------------------------------------------------|
[ALGO_MSG_MSG] [NR] Converge mode: Normal
[ALGO_MSG_MSG] [ANR] ANR internal initialize succeed
[2024-05-16 11:05:12] [ERROR] __audio_stream_init():1322 - [MPP]Audio_in_APC inited!
[ALGO_MSG_MSG] [IaaAec_GetBufferSize]Working buffer size = 84444 bytes
[ALGO_MSG_MSG] [AEC]AEC IC check pass. ver.2023.0417.0000
[ALGO_MSG_MSG] [AEC]Setting: [128][8]
[ALGO_MSG_MSG] --------------------------------------------------------------------------------
[ALGO_MSG_MSG]                                                                                 
[ALGO_MSG_MSG]                                    NEON ENABLE                                  
[ALGO_MSG_MSG]                                                                                 
[ALGO_MSG_MSG] --------------------------------------------------------------------------------
[ALGO_MSG_MSG] [AEC]Floating point mode.
[2024-05-16 11:05:12] __video_stream_start():2779 - stream start:strm_id:0
[2024-05-16 11:05:12] __video_stream_start():2779 - stream start:strm_id:1
[2024-05-16 11:05:12] [ERROR] processing_linkage_capability():140 - [STM]linkage_capability capability length 26
[2024-05-16 11:05:12] [ERROR] processing_linkage_capability():140 - [STM]linkage_capability capability length 26
[2024-05-16 11:05:12] create_and_init_sem():137 - [STM]creating initial sem...
[2024-05-16 11:05:12] init_stm_files_structure():144 - [STM]sizeof(struct stm_file) = 72
[2024-05-16 11:05:12] jpeg_stream_set_config():123 - [JPEG_STREAM]set jpeg framerate 15!
[2024-05-16 11:05:12] __video_stream_init():2483 - strm_id init:9, framerate:15, bitrate:0,u32CapWidth:640,u32CapHeight:360
[2024-05-16 11:05:12] data_sync_handle_thread():200 - [STM]register signal handler on thread:0xb509f4c0
[    8.452660] Create mi dev8 dev_type2
[    8.453343] Create mhal dev8 dev_type2
[    8.453440] dev8 dev_type2 config memory base address:0x40000000
[    8.453565] dev8 dev_type2 bAllowPreemptionSram:0 bNeedSram:0 bUsePreDevBuf:1 u32SramSize:0
[INFO]:ST_Venc_CreateChannel[708]: 
Get u32Qfactor:70

src(34-0-0-3)  dst(2-8-0-0)  4...

[2024-05-16 11:05:12] __video_stream_start():2779 - stream start:strm_id:9
[2024-05-16 11:05:12] SnapshotIndexMod_Init():1955 - [SnapshotIdx]init!
[2024-05-16 11:05:12] reload_record_adv_config():2758 - [STM]Set record pre time to 5 seconds, delay time to 60 seconds
[2024-05-16 11:05:12] stm_open():2124 - [STM][0] stm_fd is allocated. channel = 0, type = video, flags = 0x1, mode = 0x1
[2024-05-16 11:05:12] playback_init():3868 - [STM]playback init over.
[2024-05-16 11:05:12] SnapshotIndexMod_PostMsg():1843 - [SnapshotIdx]post msg(0) time(0).
[2024-05-16 11:05:12] storage_start():527 - [STM]storage start over.
[2024-05-16 11:05:12] [ERROR] ds_convert_init():85 - [DS]ds convert init successed.
[2024-05-16 11:05:12] rtsp_server_init():1681 - [RTSP]Start RTSP Server on port 554
[2024-05-16 11:05:12] rtsp_server_init():1731 - [RTSP]RTSP Server Init ended
[2024-05-16 11:05:12] inetd_register_rtsp_server():1576 - [RTSP]register rtsp server done.
[2024-05-16 11:05:12] [ERROR][tapoCare]tapo_care.c:241(tapocare_box_start) - ringbuffer_attach error:type: rb_id:10200

[2024-05-16 11:05:12] cap_start():41 - [CAP]CAP start ......
[2024-05-16 11:05:12] [ERROR] avdm_audio_recv_cb():3321 - [AVDM]put audio buffer to avdm failed
add package code_type 0
av_codec = 0
add package code_type 0
av_codec = 0
add package code_type 6
av_codec = 6
add package code_type 6
av_codec = 6
[    8.726877] [ss_gpi_intc_domain_alloc] hw:88 -> v:82
[    8.735263] [ss_gpi_intc_domain_alloc] hw:12 -> v:83
[    8.735774] [ss_gpi_intc_domain_alloc] hw:13 -> v:84
[2024-05-16 11:05:12] [ERROR] camera_image_exposure_set():2595 - [CAMERA]MI_ISP_AE_SetExposureLimit over.
[2024-05-16 11:05:12] image_start():1583 - [IMAGE]Image start over.
[2024-05-16 11:05:12] dn_switch_start():1320 - [DN_SWITCH]start dn_switch_start  
[2024-05-16 11:05:12] dn_switch_init():1062 - [DN_SWITCH]dn_switch init start.

[2024-05-16 11:05:12] [ERROR] dn_switch_init():1100 - [DN_SWITCH]dn_switch,choose WL algorithm
[2024-05-16 11:05:12] record_plan_start():261 - [RECORD_PLAN]start over, ret[0]
[2024-05-16 11:05:12] msg_alarm_start():1796 - [MSG_ALARM]msg alarm start over.
[2024-05-16 11:05:12] hsr_alarm_start():1304 - [HSR]hsr_alarm start over.
[2024-05-16 11:05:12] vd_alarm_start():1296 - [VD_ALARM]vd_alarm start over.
[2024-05-16 11:05:12] ptd_alarm_start():1300 - [PTD_ALARM]ptd_alarm start over.
[2024-05-16 11:05:12] bcd_alarm_start():794 - [BCD_ALARM]bcd_alarm start over.
[2024-05-16 11:05:12] bark_alarm_start():794 - [BARK_ALARM]bark_alarm start over.
[2024-05-16 11:05:12] meow_alarm_start():794 - [MEOW_ALARM]meow_alarm start over.
[2024-05-16 11:05:12] glass_alarm_start():794 - [GLASS_ALARM]glass_alarm start over.
[2024-05-16 11:05:12] md_alarm_start():1656 - [MD_ALARM]md alarm start over.
[2024-05-16 11:05:12] cd_alarm_start():1758 - [CD]cd_alarm start over.
[2024-05-16 11:05:12] [ERROR] ams_start():440 - [AMS] ams version: 3.11.0.2501-f780de4
[2024-05-16 11:05:12] [ERROR] ams_start():444 - [AMS] ams init start: 8645282
[2024-05-16 11:05:12] p2p_start():34 - [P2P]p2p module started. version: 2.0

debug_tools_coredump_start()-99 - [DEBUG_TOOLS]USAGE:input "killall -10 main" to enable coredump 
[2024-05-16 11:05:12] upnpc_start():1065 - [UPNPC]start over
[2024-05-16 11:05:12] mb_start():727 - [MB]mb start over.
[2024-05-16 11:05:12] StreamTrans_SetConfig():192 - [Transmit]default_bufsize(65536) relay_bufsize(192512)
[2024-05-16 11:05:12] __video_stream_init():2483 - strm_id init:2, framerate:15, bitrate:0,u32CapWidth:352,u32CapHeight:288
[2024-05-16 11:05:12] http_server_init():1948 - [HTTP]Start HTTP Server on port 8800
[2024-05-16 11:05:12] __video_stream_start():2779 - stream start:strm_id:2
[2024-05-16 11:05:12] [ERROR] dla_ctx_init():138 - [libdla] libdla version: 3.11.0.2501-f780de4
[2024-05-16 11:05:12] http_server_init():1986 - [HTTP]HTTP Server Init ended
[2024-05-16 11:05:12] inetd_register_http_server():1832 - [HTTP]register http server done.
[2024-05-16 11:05:12] [ERROR] ds_register_action():826 - [DS]Action [video.force_iframe] has exist.
[2024-05-16 11:05:12] http_reload():3301 - [HTTP]config changes http_reload
[2024-05-16 11:05:12] record_plan_action_callback():2238 - [STM]record_plan new rec type:(null)
[2024-05-16 11:05:12] http_reload():3301 - [HTTP]config changes http_reload
[2024-05-16 11:05:12] http_reload():3301 - [HTTP]config changes http_reload
[2024-05-16 11:05:12] http_reload():3301 - [HTTP]config changes http_reload
(osd_set_logo 1010)exec function pass
(osd_set_logo 1015)exec function pass
(osd_set_logo 1022)exec function pass
(osd_set_time 1118)exec function pass
(osd_set_time 1132)exec function pass
(osd_set_text 1200)exec function pass
(osd_set_text 1217)exec function pass
(osd_set_logo 1010)exec function pass
(osd_set_logo 1015)exec function pass
(osd_set_logo 1022)exec function pass
(osd_set_time 1118)exec function pass
(osd_set_time 1132)exec function pass
[MAJOR]: ispversion(1) in sdk, ispversion(1) in binfile.
[MINOR]: ispversion(2) in sdk, ispversion(2) in binfile.
[pAF_SetMotor-0230] Error paramters!! u16MinMotorPos = 320, u16MaxMotorPos = 700, u16HWMinMotorPos = 0, u16HWMaxMotorPos = 0 
(osd_set_text 1200)exec function pass
(osd_set_text 1217)exec function pass
(osd_set_logo 1010)exec function pass
(osd_set_logo 1015)exec function pass
(osd_set_logo 1022)exec function pass
(osd_set_time 1118)exec function pass
(osd_set_time 1132)exec function pass
******************** Load api bin Success - /tmp/base-files/cfg/isp_day.bin ********************
(osd_set_text 1200)exec function pass
(osd_set_text 1217)exec function pass
[2024-05-16 11:05:12] osd_start():2528 - [OSD]Osd start over.
[    8.915355] client [727] connected, module:ipu
[is_cal] wlan-manager: driver is not ready, wait...
[MAJOR]: ispversion(1) in sdk, ispversion(1) in binfile.
[MINOR]: ispversion(2) in sdk, ispversion(2) in binfile.
[pAF_SetMotor-0230] Error paramters!! u16MinMotorPos = 320, u16MaxMotorPos = 700, u16HWMinMotorPos = 0, u16HWMaxMotorPos = 0 
******************** Load api bin Success - /tmp/base-files/cfg/isp_day.bin ********************
[2024-05-16 11:05:13] [ERROR] camera_image_exposure_set():2595 - [CAMERA]MI_ISP_AE_SetExposureLimit over.
[2024-05-16 11:05:13] delay_setting_light_timer_handle():2485 - [CAMERA]Switch to DAY, WTL OFF
[2024-05-16 11:05:13] http_reload():3301 - [HTTP]config changes http_reload
[2024-05-16 11:05:13] delay_setting_light_timer_handle():2490 - [CAMERA]Switch to DAY, IR OFF
[2024-05-16 11:05:13] record_stop():4114 - [STM]record stopped
[2024-05-16 11:05:13] [ERROR] system_get_wan_phy_status():596 - [NIFC]Get wan phy status: LINK_DOWN
[2024-05-16 11:05:13] sntpc_reload():918 - [SNTPC]link_status change to :0
[2024-05-16 11:05:13] rtsp_reload():2892 - [RTSP]config changes rtsp_reload
[2024-05-16 11:05:13] upnpc_reload():1025 - [UPNPC]reload over
[2024-05-16 11:05:13] http_reload():3301 - [HTTP]config changes http_reload
[2024-05-16 11:05:13] [ERROR] led_rule_call_handle():112 - [LEDRULE]receive led_state: [8]
[is_cal] wlan-manager: driver is not ready, wait...
[2024-05-16 11:05:14] [ERROR][tapoCare]tapo_care.c:179(attach_tapocare_ringbuffer) - ringbuffer_attach error: rb_id:10200

[2024-05-16 11:05:14] __video_stream_init():2483 - strm_id init:6, framerate:15, bitrate:0,u32CapWidth:800,u32CapHeight:448
[2024-05-16 11:05:14] __video_stream_start():2779 - stream start:strm_id:6
[dms_detach_event()]:[850]: detach msg[20486] handler[0xab575]
[dms_detach_event()]:[850]: detach msg[20487] handler[0xab561]
[ALGO_MSG_MSG] [IaaAec_GetBufferSize]Working buffer size = 84444 bytes
[ALGO_MSG_MSG] [AEC]AEC IC check pass. ver.2023.0417.0000
[ALGO_MSG_MSG] [AEC]Setting: [128][8]
[ALGO_MSG_MSG] --------------------------------------------------------------------------------
[ALGO_MSG_MSG]                                                                                 
[ALGO_MSG_MSG]                                    NEON ENABLE                                  
[ALGO_MSG_MSG]                                                                                 
[ALGO_MSG_MSG] --------------------------------------------------------------------------------
[ALGO_MSG_MSG] [AEC]Floating point mode.
[ALGO_MSG_MSG] [IaaAec_GetBufferSize]Working buffer size = 84444 bytes
[ALGO_MSG_MSG] [AEC]AEC IC check pass. ver.2023.0417.0000
[ALGO_MSG_MSG] [AEC]Setting: [128][8]
[ALGO_MSG_MSG] --------------------------------------------------------------------------------
[ALGO_MSG_MSG]                                                                                 
[ALGO_MSG_MSG]                                    NEON ENABLE                                  
[ALGO_MSG_MSG]                                                                                 
[ALGO_MSG_MSG] --------------------------------------------------------------------------------
[ALGO_MSG_MSG] [AEC]Floating point mode.
[2024-05-16 11:05:14] aecns_init():136 - [AMS] [TPAECNS] init ok!
[2024-05-16 11:05:14] [ERROR] ams_get_mcu_bpi_mode():3299 - [AMS] not battery camera,file /dev/mcu_info not exist

[2024-05-16 11:05:14] [ERROR] md_load_det():1110 - [AMS] read PIR_CONFIG failed, set default pir sensitivity 
[2024-05-16 11:05:14] [ERROR] sed_dla_reload_det():34 - [AMS] load co alarm params failed.
[2024-05-16 11:05:14] [ERROR] ams_main_progress():405 - [AMS] ams init finish: 10883755
[is_cal] wlan-manager: driver is not ready, wait...
[2024-05-16 11:05:15] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:15] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:15] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:15] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:15] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:15] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:15] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:15] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:15] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:15] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:15] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:15] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:15] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:15] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:15] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:15] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:15] onvif_discv_start():166 - [ONVIF]Onvif discovery start
[2024-05-16 11:05:15] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:15] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:15] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:15] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:15] [ERROR][CloudIot]cloud_iot_common.c:2447(cloud_iot_send_ext_message) - send msg:$ext/service/ntp/8021CB8AEFE4885EC5F7E2A481AE1C5D23428EB9/get
payload = {"deviceRequestTime": 1715857515928}
[2024-05-16 11:05:15] [ERROR][CloudIot]mqtt_client.c:188(mqtt_publish) - mqtt client ctx is null.

[2024-05-16 11:05:15] mqtt_send_ntp_request():2382 - [CloudIot]req ntp err
[2024-05-16 11:05:15] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:15] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:15] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:15] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:15] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:15] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR][tapoCare]tapo_care.c:184(attach_tapocare_ringbuffer) - ringbuffer_attach success: rb_id:10200

[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] http_client_connect_close():207 - [CloudIot]http 0 conn err: 1006.
[2024-05-16 11:05:16] [ERROR][CloudIot]cloud_iot_ipc.c:2990(cloud_http_message_handler) - http client close, HTTP event type: 5.

[2024-05-16 11:05:16] [ERROR][CloudIot]cloud_iot_ipc.c:2947(http_auth_fail_cb) - http auth timeout, retry in 16s.

[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:16] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:16] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:16] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:16] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:16] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:17] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:17] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:17] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[is_cal] wireless is cal, and check success
[2024-05-16 11:05:17] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:17] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:17] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:17] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_petd_result():577 - [AMS] mark_motion_petd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] petd_dla_process_dev():1130 - [AMS] mark_motion_petd_result error.
[2024-05-16 11:05:17] [ERROR] petd_dla_trigger_dev():1602 - [AMS] petd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_pd_result():684 - [AMS] mark_motion_pd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] pd_dla_process_dev():1076 - [AMS] mark_motion_pd_result error.
[2024-05-16 11:05:17] [ERROR] pd_dla_trigger_dev():1557 - [AMS] pd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] mark_motion_vd_result():885 - [AMS] mark_motion_vd_result: empty fg!
[2024-05-16 11:05:17] [ERROR] vd_dla_process_dev():1355 - [AMS] mark_motion_vd_result error.
[2024-05-16 11:05:17] [ERROR] vd_dla_trigger_dev():1590 - [AMS] vd_dla_process failed.
[2024-05-16 11:05:17] [ERROR] phy_status_update():50 - [NIFC]Link_status: LINK_DOWN <---> Path_status: LINK_DOWN

===>hotplug_ethernet out
[2024-05-16 11:05:22] [ERROR][CloudIot]cloud_iot_common.c:2447(cloud_iot_send_ext_message) - send msg:$ext/service/ntp/8021CB8AEFE4885EC5F7E2A481AE1C5D23428EB9/get
payload = {"deviceRequestTime": 1715857522790}
[2024-05-16 11:05:22] [ERROR][CloudIot]mqtt_client.c:188(mqtt_publish) - mqtt client ctx is null.

[2024-05-16 11:05:22] mqtt_send_ntp_request():2382 - [CloudIot]req ntp err
[2024-05-16 11:05:25] [ERROR] led_rule_call_handle():112 - [LEDRULE]receive led_state: [8]
[2024-05-16 11:05:25] dhcps_start_cb():1060 - [DHCPS]Start DHCP server
Successfully initialized wpa_supplicant
rfkill: Cannot open RFKILL control device
[2024-05-16 11:05:26] [ERROR] led_rule_call_handle():112 - [LEDRULE]receive led_state: [3]
ffs start...
Monitor: receive NVMP_START_DONE. pid:727
[2024-05-16 11:05:26] nvmp_print_start_done():313 - [NVMP]Main progress start done
[2024-05-16 11:05:26] [ERROR] ds_handle():2562 - [DS]Signal method is illegal.
[2024-05-16 11:05:26] [ERROR] ds_handle():2562 - [DS]Signal method is illegal.
dnsd: accepting UDP packets on 0.0.0.0:53
[dms_detach_event()]:[850]: detach msg[38] handler[0x1ce09]
[2024-05-16 11:05:29] [ERROR] play_system_state_audio_ex():622 - [SPEAKER]play_system_state_audio_ex: open audio file error. (/lib/audio/pls_use_tp_app.g711)

[2024-05-16 11:05:35] [ERROR][CloudIot]cloud_iot_common.c:2447(cloud_iot_send_ext_message) - send msg:$ext/service/ntp/8021CB8AEFE4885EC5F7E2A481AE1C5D23428EB9/get
payload = {"deviceRequestTime": 1715857535790}
[2024-05-16 11:05:35] [ERROR][CloudIot]mqtt_client.c:188(mqtt_publish) - mqtt client ctx is null.

[2024-05-16 11:05:35] mqtt_send_ntp_request():2382 - [CloudIot]req ntp err
[2024-05-16 11:05:37] [ERROR] http_client_connect_close():207 - [CloudIot]http 0 conn err: 1006.
[2024-05-16 11:05:37] [ERROR][CloudIot]cloud_iot_ipc.c:2990(cloud_http_message_handler) - http client close, HTTP event type: 5.

[2024-05-16 11:05:37] [ERROR][CloudIot]cloud_iot_ipc.c:2947(http_auth_fail_cb) - http auth timeout, retry in 16s.

[2024-05-16 11:05:58] [ERROR] http_client_connect_close():207 - [CloudIot]http 0 conn err: 1006.
[2024-05-16 11:05:58] [ERROR][CloudIot]cloud_iot_ipc.c:2990(cloud_http_message_handler) - http client close, HTTP event type: 5.

[2024-05-16 11:05:58] [ERROR][CloudIot]cloud_iot_ipc.c:2947(http_auth_fail_cb) - http auth timeout, retry in 16s.

[2024-05-16 11:06:00] [ERROR][CloudIot]cloud_iot_common.c:2447(cloud_iot_send_ext_message) - send msg:$ext/service/ntp/8021CB8AEFE4885EC5F7E2A481AE1C5D23428EB9/get
payload = {"deviceRequestTime": 1715857560790}
[2024-05-16 11:06:00] [ERROR][CloudIot]mqtt_client.c:188(mqtt_publish) - mqtt client ctx is null.

[2024-05-16 11:06:00] mqtt_send_ntp_request():2382 - [CloudIot]req ntp err
[2024-05-16 11:06:19] [ERROR] http_client_connect_close():207 - [CloudIot]http 0 conn err: 1006.
[2024-05-16 11:06:19] [ERROR][CloudIot]cloud_iot_ipc.c:2990(cloud_http_message_handler) - http client close, HTTP event type: 5.

[2024-05-16 11:06:19] [ERROR][CloudIot]cloud_iot_ipc.c:2947(http_auth_fail_cb) - http auth timeout, retry in 16s.

[2024-05-16 11:06:25] [ERROR][CloudIot]cloud_iot_common.c:2447(cloud_iot_send_ext_message) - send msg:$ext/service/ntp/8021CB8AEFE4885EC5F7E2A481AE1C5D23428EB9/get
payload = {"deviceRequestTime": 1715857585790}
[2024-05-16 11:06:25] [ERROR][CloudIot]mqtt_client.c:188(mqtt_publish) - mqtt client ctx is null.

[2024-05-16 11:06:25] mqtt_send_ntp_request():2382 - [CloudIot]req ntp err
[2024-05-16 11:06:40] [ERROR] http_client_connect_close():207 - [CloudIot]http 0 conn err: 1006.
[2024-05-16 11:06:40] [ERROR][CloudIot]cloud_iot_ipc.c:2990(cloud_http_message_handler) - http client close, HTTP event type: 5.

[2024-05-16 11:06:40] [ERROR][CloudIot]cloud_iot_ipc.c:2947(http_auth_fail_cb) - http auth timeout, retry in 16s.

delay_set_cpu_scaling_max_freq to 800000, ret = 0
[2024-05-16 11:06:50] [ERROR][CloudIot]cloud_iot_common.c:2447(cloud_iot_send_ext_message) - send msg:$ext/service/ntp/8021CB8AEFE4885EC5F7E2A481AE1C5D23428EB9/get
payload = {"deviceRequestTime": 1715857610790}
[2024-05-16 11:06:50] [ERROR][CloudIot]mqtt_client.c:188(mqtt_publish) - mqtt client ctx is null.

[2024-05-16 11:06:50] mqtt_send_ntp_request():2382 - [CloudIot]req ntp err
[2024-05-16 11:07:01] [ERROR] http_client_connect_close():207 - [CloudIot]http 0 conn err: 1006.
[2024-05-16 11:07:01] [ERROR][CloudIot]cloud_iot_ipc.c:2990(cloud_http_message_handler) - http client close, HTTP event type: 5.

[2024-05-16 11:07:01] [ERROR][CloudIot]cloud_iot_ipc.c:2947(http_auth_fail_cb) - http auth timeout, retry in 16s.

[2024-05-16 11:07:15] [ERROR][CloudIot]cloud_iot_common.c:2447(cloud_iot_send_ext_message) - send msg:$ext/service/ntp/8021CB8AEFE4885EC5F7E2A481AE1C5D23428EB9/get
payload = {"deviceRequestTime": 1715857635790}
[2024-05-16 11:07:15] [ERROR][CloudIot]mqtt_client.c:188(mqtt_publish) - mqtt client ctx is null.

[2024-05-16 11:07:15] mqtt_send_ntp_request():2382 - [CloudIot]req ntp err
[2024-05-16 11:07:22] [ERROR] http_client_connect_close():207 - [CloudIot]http 0 conn err: 1006.
[2024-05-16 11:07:22] [ERROR][CloudIot]cloud_iot_ipc.c:2990(cloud_http_message_handler) - http client close, HTTP event type: 5.

[2024-05-16 11:07:22] [ERROR][CloudIot]cloud_iot_ipc.c:2947(http_auth_fail_cb) - http auth timeout, retry in 16s.
```
