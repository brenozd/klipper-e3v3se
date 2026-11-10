Welcome to the Klipper project!

[![Klipper](docs/img/klipper-logo-small.png)](https://www.klipper3d.org/)

https://www.klipper3d.org/

The Klipper firmware controls 3d-Printers. It combines the power of a
general purpose computer with one or more micro-controllers. See the
[features document](https://www.klipper3d.org/Features.html) for more
information on why you should use the Klipper software.

Start by [installing Klipper software](https://www.klipper3d.org/Installation.html).

Klipper software is Free Software. See the [license](COPYING) or read
the [documentation](https://www.klipper3d.org/Overview.html). We
depend on the generous support from our
[sponsors](https://www.klipper3d.org/Sponsors.html).

## Acknowledgements

This repository is Klipper
([Klipper3d/klipper](https://github.com/Klipper3d/klipper), GPL-3.0) at
`56a9c605e121c6560f5c8b6c0e33bdda86de69a1`, plus Ender-3 V3 SE support
integrated from the three community repositories below. All of them are
licensed under the GNU General Public License v3.0 (`COPYING:2`,
"Version 3, 29 June 2007").

The serial-bridge code in the jpcurti entry originates from E4ST2W3ST's
unmerged pull request Klipper3d/klipper#6444
(`6469418d73be6743a7130b50fdb5a57d311435ca`).

### fpnewton/klipper-ender3v3se

<https://github.com/fpnewton/klipper-ender3v3se> — snapshot
`d24980c3010a50c201cf7364987c14d42961c11e` (2026-05-04). Licence:
GPL-3.0.

- Authors credited: Fraser Newton, F_ig, Tom Hiller.
- Used here: `config.ender3v3se` and `make-ender3v3se.sh`
  (`3ba25041`, `e15279af`, `e284add0`, `b8f0bfb3`); `e3v3se_docs/`
  (`b2bb4d21`, `afe8af18`, `87030b6b`); the background of the Z-offset
  sign fix folded into `klippy/extras/prtouch.py` (`95704c33`,
  `92bece11`).
- Modified here: the defconfig is kept verbatim; the prtouch Z-offset
  fix was rewritten rather than copied (upstream issue
  `0xD34D/klipper_ender3_v3_se#32`); no CI workflow or prebuilt `.bin`
  was taken.

### jpcurti/ender3-v3-se-klipper-with-display

<https://github.com/jpcurti/ender3-v3-se-klipper-with-display> —
snapshot `d74d36bb69bd8c561a169fd99e8c83e254318562` (2026-07-29).
Licence: GPL-3.0.

- Authors credited: Joao Curti, LeandroSQ, SupremeCake17, Shubham Patel,
  Bogdan, rmilki.
- Used here: `klippy/extras/serial_bridge.py` and the matching MCU
  sources (`cd1e82a7`, `0c84c5ad`); `klippy/extras/e3v3se_display.py`,
  `TJC3224.py`, `printerInterface.py` (`5536a21b`, `a34fd9a5`,
  `09ec47c7` plus 53 later commits); `klippy/extras/{prtouch,hx711s,
  dirzctl,filter}.py` and `src/{dirzctl,hx711s}.c`.
- Modified here: the display files are taken as one snapshot instead of
  replaying 56 commits; the `gcode_move.py` `p[:4]` change
  (`72e925e5`) was deliberately **not** imported (it is a no-op on
  current Klipper); the prtouch Z-offset arithmetic was replaced (#32);
  line endings normalised and trailing whitespace stripped in the
  imported Python/C files.

### 0xD34D/klipper_ender3_v3_se

<https://github.com/0xD34D/klipper_ender3_v3_se> — snapshot
`7e61c1ccda2f2e8f6bd518997f3833319da03a20` (2026-08-17); the base layer
of the other two forks. Licence: GPL-3.0.

- Authors credited: 0xD34D, schnoog, Supremecake17.
- Used here: `klippy/extras/{prtouch,hx711s,dirzctl,filter}.py` and
  `src/{dirzctl,hx711s}.c` (`311db3db`, `b41a93be`, `7d8057a8`,
  `63626421`, `4bb5bb2d`); `MCU_stepper.get_pin_info()` in
  `klippy/stepper.py` (`2b3e8411`); the `src/Makefile` hunk
  (`554b0301`).
- Modified here: the `src/Makefile` line was re-anchored on
  `CONFIG_HAVE_GPIO` after upstream renamed `CONFIG_HAVE_GPIO_ADC` to
  `CONFIG_WANT_ADC`; open issue #32 is addressed separately in
  `klippy/extras/prtouch.py`.
