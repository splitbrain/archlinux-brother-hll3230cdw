# Brother HL-L3230CDW for ArchLinux

This is a `PKGBUILD` to install the Brother CUPS drivers for the HL-L3230CDW printer on ArchLinux.

It's based on the AUR package for the [HL-L2395DW package](https://aur.archlinux.org/packages/brother-hll2395dw/). However it does not even try to fix the weird package locations Brother used (several of them are hard coded inside the binaries). Instead it simply extracts the RPM package, and symlinks the two files that CUPS needs.

Because of the non-standard paths, this package has not been pushed to AUR.

## Installation

Clone the repository and run

    $> makepkg
    #> sudo pacman -U brother-*.pkg.tar.xz

Then open the CUPS admin on http://localhost:631, add a new printer and pick the `Brother HL-L3230CDW CUPS` driver.

## Directory Structure

This is the structure the package set up.

```
\
├── opt
│   └── brother
│       └── Printers
│           └── hll3230cdw
│               ├── cupswrapper
│               │   ├── brother_hll3230cdw_printer_en.ppd
│               │   ├── brother_lpdwrapper_hll3230cdw
│               │   └── cupswrapperhll3230cdw
│               ├── inf
│               │   ├── brhll3230cdwfunc
│               │   ├── brhll3230cdwrc
│               │   ├── ImagingArea
│               │   ├── lut
│               │   │   ├── 0600-c_cache17.bin
│               │   │   ├── 0600-c-TS_cache17.bin
│               │   │   ├── 0600-k_cache17.bin
│               │   │   ├── 0600-k-TS_cache17.bin
│               │   │   ├── 0600-m_cache17.bin
│               │   │   ├── 0600-m-TS_cache17.bin
│               │   │   ├── 0600-y_cache17.bin
│               │   │   ├── 0600-y-TS_cache17.bin
│               │   │   ├── capt-c_cache17.bin
│               │   │   ├── capt-c-TS_cache17.bin
│               │   │   ├── capt-k_cache17.bin
│               │   │   ├── capt-k-TS_cache17.bin
│               │   │   ├── capt-m_cache17.bin
│               │   │   ├── capt-m-TS_cache17.bin
│               │   │   ├── capt-y_cache17.bin
│               │   │   └── capt-y-TS_cache17.bin
│               │   ├── paperinfij2
│               │   └── setupPrintcapij
│               ├── LICENSE_ENG.txt
│               ├── LICENSE_JPN.txt
│               └── lpd
│                   ├── brhll3230cdwfilter
│                   └── filter_hll3230cdw
└── usr
    ├── bin
    │   └── brprintconf_hll3230cdw
    ├── lib
    │   └── cups
    │       └── filter
    │           └── brother_lpdwrapper_hll3230cdw -> /opt/brother/Printers/hll3230cdw/cupswrapper/brother_lpdwrapper_hll3230cdw
    └── share
        └── cups
            └── model
                └── brother_hll3230cdw_printer_en.ppd -> /opt/brother/Printers/hll3230cdw/cupswrapper/brother_hll3230cdw_printer_en.ppd
```
