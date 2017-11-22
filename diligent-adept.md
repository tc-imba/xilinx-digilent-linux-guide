# Digilent Adept

## Installation

First, download and install Runtime and Utilities on 
[Download Page](https://reference.digilentinc.com/reference/software/adept/start).

The installed utility is named as `djtgcfg` (Digilent JTAG Config Utility).

## Connecting the board

Connect the board with USB and run the command
```
$ djtgcfg enum
```

Then your board should be listed, for example
```
Found 1 device(s)

Device: Nexys2
    Product Name:   Onboard USB
    User Name:      Nexys2
    Serial Number:  1005XXXXXXXX
```

If you can find your board, type (suppose your board is Nexys2)
```
$ djtgcfg init -d Nexys2
```

The output should be like this
```
Initializing scan chain...
Found Device ID: f504XXXX
Found Device ID: 21c2XXXX

Found 2 device(s):
    Device 0: XC3S1200E
    Device 1: XCF04S
```

Usually you will need to use device 0, so the index will be 0.

At last, program your .bit file (suppose your board is Nexys2)
```
$ djtgcfg prog -f xxx.bit -d Nexys2 -i 0
```

It should output
```
Programming device. Do not touch your board. This may take a few minutes...
Programming succeeded.
```

Notice that if you didn't set clock as JTAG, a warning will be spawned in this stage.

Please generate your .bit file again with the right clock, or something unexpected will happen.
