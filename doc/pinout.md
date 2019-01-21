The WavDJ VM-108 has a single 8 pin RJ45 connector for interfacing with a computer.

Internally the main processor (unknown: 005-8223M4-31 08) communicates to a subboard using TTL that is translated to RS232 levels via a DS143232CM chip.

## DS143232CM Pinout

    C1+   1---16  VCC
    V+    2   15  GND
    C1-   3   14  Dout1
    C2+   4   13  Rin1
    C2-   5   12  Rout1
    V-    6   11  Din1
    Dout2 7   10  Din2
    Rin   8----9  Rout2

*Din2 is shorted to ground*

## RJ45 Pinout

    1 - CTS (DE-9 Pin 8)
    2 - RTS (DE-9 Pin 7)
    3 - RD (DE-9 Pin 2)
    4 - TD (DE-9 Pin 3)
    5 - GND (DE-9 Pin 5 or PS/2 Pin 3) ??
    6 - GND (DE-9 Pin 5 or PS/2 Pin 3) ??
    7 - 5VDC (PS/2 Pin 4)
    8 - 5VDC (PS/2 Pin 4)

## Labeled photo of RS232 Sub board
![Labeled RS232 Photo](./RS232BoardLabeled.png?raw=true "Labeled Photo")
