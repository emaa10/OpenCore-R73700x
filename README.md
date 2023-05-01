# OpenCore-R73700x

Opencore config for my PC.
Current OC version: 0.8.8

Specs:
- RX 6600 XT
- Ryzen 7 3700x
- 500GB Samsung 980 SSD
- 32GB G.Skill Aegis RAM
- ASRock X570 Phantom Gaming 4


Not working:
- Ethernet

Fixed bugs
- <strike>Constant SSD speed (going up and down randomly)</strike>
-> fixed by setting the `SetApfsTrimTimeout` (trim timeout on boot) to `4294967295` (maximum value)