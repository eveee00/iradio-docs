---
title: (TCM) Dumping FW
layout: default
parent: (TCM) Firmware, etc
nav_order: 2
---

1. Get a 3.3v SPI flasher
2. Connect the chip
3. enable spi
4. compile flashrom
5. sudo flashrom -p linux_spi:dev=/dev/spidev0.0,spispeed=512

*Also yes, this is STILL not done, im just focused on writing other stuff*