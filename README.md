# GOBOY2

## Introduction

As the name implies, this is my second try to develop a gameboy emulator in go. 
The first one was capable of playing Tetris and even some other games, but I wanted to improve
the accuracy of emulation. To do so I've decided to rewrite the CPU to use some kind of *micro-opcodes*
which really helped a lot.

## Boot-Roms

Due to the fact, that the data of the rom chips of the original gameboy is IP of Nintendo. This data
is stripped from the code. It could be added by adding the binary data to `mmu/bootom.go`. 
The other option is to start the emulator using the `-noboot` option.

## Deployment

You might need to install the SDL2 libs for your system. 

## Input

The default key-map is as follows:

```
	Up, Down, 
	Left, Right --> Arrow Keys

	Start       --> Return 
	Select      --> Backspace
	
	A           --> X-Key
	B           --> Y-Key
```



## Tests

### Blargg

| Test             | Result |
| ---------------- | ------ |
| `cgb_sound`      | ❌ |
| `cpu_instrs`     | ✅ |
| `dmg_sound`      | ❌ |
| `instr_timing`   | ✅ |
| `interrupt_time` | ✅ |
| `mem_timing`     | ✅ |
| `mem_timing-2`   | ✅ |
| `oam_bug`        | ❌ |
| `halt_bug`       | ✅ |

### Mooneye

With the [tests from the 18. Apr. 2020](https://github.com/Gekkio/mooneye-gb/commit/6b9488fa3e7da033a3c33c55ac94476c0e8368b0) the emulator currently gets the following results:

#### General

| Test                                                 | Result |
| ---------------------------------------------------- | ------ |
| `acceptance -> add_sp_e_timing`                      | ✅     |
| `acceptance -> bits -> mem_oam`                      | ✅     |
| `acceptance -> bits -> reg_f`                        | ✅     |
| `acceptance -> call_cc_timing`                       | ✅     |
| `acceptance -> call_cc_timing2`                      | ✅     |
| `acceptance -> call_timing`                          | ✅     |
| `acceptance -> call_timing2`                         | ✅     |
| `acceptance -> div_timing`                           | ✅     |
| `acceptance -> ei_sequence`                          | ✅     |
| `acceptance -> ei_timing`                            | ✅     |
| `acceptance -> halt_ime0_ei`                         | ✅     |
| `acceptance -> halt_ime0_nointr_timing`              | ❌     |
| `acceptance -> halt_ime1_timing`                     | ✅     |
| `acceptance -> if_ie_registers`                      | ✅     |
| `acceptance -> instr -> daa`                         | ✅     |
| `acceptance -> interrupts -> ie_push`                | ✅     |
| `acceptance -> intr_timing`                          | ✅     |
| `acceptance -> jp_cc_timing`                         | ✅     |
| `acceptance -> jp_timing`                            | ✅     |
| `acceptance -> ld_hl_sp_e_timing`                    | ✅     |
| `acceptance -> oam_dma -> basic`                     | ✅     |
| `acceptance -> oam_dma -> reg_read`                  | ✅     |
| `acceptance -> oam_dma_restart`                      | ✅     |
| `acceptance -> oam_dma_start`                        | ✅     |
| `acceptance -> oam_dma_timing`                       | ✅     |
| `acceptance -> pop_timing`                           | ✅     |
| `acceptance -> ppu -> intr_2_0_timing`               | ❌     |
| `acceptance -> ppu -> intr_2_mode0_timing`           | ❌     |
| `acceptance -> ppu -> intr_2_mode0_timing_sprites`   | ❌     |
| `acceptance -> ppu -> intr_2_mode3_timing`           | ❌     |
| `acceptance -> ppu -> intr_2_oam_ok_timing`          | ❌     |
| `acceptance -> ppu -> stat_irq_blocking`             | ❌     |
| `acceptance -> ppu -> stat_lyc_onoff`                | ❌     |
| `acceptance -> push_timing`                          | ✅     |
| `acceptance -> rapid_di_ei`                          | ✅     |
| `acceptance -> ret_cc_timing`                        | ✅     |
| `acceptance -> ret_timing`                           | ✅     |
| `acceptance -> reti_intr_timing`                     | ✅     |
| `acceptance -> reti_timing`                          | ✅     |
| `acceptance -> rst_timing`                           | ✅     |
| `acceptance -> timer -> div_write`                   | ✅     |
| `acceptance -> timer -> rapid_toggle`                | ✅     |
| `acceptance -> timer -> tim00`                       | ✅     |
| `acceptance -> timer -> tim00_div_trigger`           | ✅     |
| `acceptance -> timer -> tim01`                       | ✅     |
| `acceptance -> timer -> tim01_div_trigger`           | ✅     |
| `acceptance -> timer -> tim10`                       | ✅     |
| `acceptance -> timer -> tim10_div_trigger`           | ✅     |
| `acceptance -> timer -> tim11`                       | ✅     |
| `acceptance -> timer -> tim11_div_trigger`           | ✅     |
| `acceptance -> timer -> tima_reload`                 | ✅     |
| `acceptance -> timer -> tima_write_reloading`        | ✅     |
| `acceptance -> timer -> tma_write_reloading`         | ✅     |
| `emulator-only -> mbc1 -> bits_bank1`                | ✅     |
| `emulator-only -> mbc1 -> bits_bank2`                | ✅     |
| `emulator-only -> mbc1 -> bits_mode`                 | ✅     |
| `emulator-only -> mbc1 -> bits_ramg`                 | ✅     |
| `emulator-only -> mbc1 -> multicart_rom_8Mb`         | ✅     |
| `emulator-only -> mbc1 -> ram_256kb`                 | ✅     |
| `emulator-only -> mbc1 -> ram_64kb`                  | ✅     |
| `emulator-only -> mbc1 -> rom_16Mb`                  | ✅     |
| `emulator-only -> mbc1 -> rom_1Mb`                   | ✅     |
| `emulator-only -> mbc1 -> rom_2Mb`                   | ✅     |
| `emulator-only -> mbc1 -> rom_4Mb`                   | ✅     |
| `emulator-only -> mbc1 -> rom_512kb`                 | ✅     |
| `emulator-only -> mbc1 -> rom_8Mb`                   | ✅     |
| `emulator-only -> mbc2 -> bits_ramg`                 | ✅     |
| `emulator-only -> mbc2 -> bits_romb`                 | ✅     |
| `emulator-only -> mbc2 -> bits_unused`               | ✅     |
| `emulator-only -> mbc2 -> ram`                       | ✅     |
| `emulator-only -> mbc2 -> rom_1Mb`                   | ✅     |
| `emulator-only -> mbc2 -> rom_2Mb`                   | ✅     |
| `emulator-only -> mbc2 -> rom_512kb`                 | ✅     |
| `emulator-only -> mbc5 -> rom_16Mb`                  | ✅     |
| `emulator-only -> mbc5 -> rom_1Mb`                   | ✅     |
| `emulator-only -> mbc5 -> rom_2Mb`                   | ✅     |
| `emulator-only -> mbc5 -> rom_32Mb`                  | ✅     |
| `emulator-only -> mbc5 -> rom_4Mb`                   | ✅     |
| `emulator-only -> mbc5 -> rom_512kb`                 | ✅     |
| `emulator-only -> mbc5 -> rom_64Mb`                  | ✅     |
| `emulator-only -> mbc5 -> rom_8Mb`                   | ✅     |


#### DMG

| Test                                                 | Result |
| ---------------------------------------------------- | ------ |
| `acceptance -> bits -> unused_hwio-GS`               | ✅     |
| `acceptance -> boot_div-dmgABCmgb`                   | ✅     |
| `acceptance -> boot_hwio-dmgABCmgb`                  | ✅     |
| `acceptance -> boot_regs-dmgABC`                     | ✅     |
| `acceptance -> di_timing-GS`                         | ❌     |
| `acceptance -> halt_ime1_timing2-GS`                 | ❌     |
| `acceptance -> oam_dma -> sources-GS`                | ✅     |
| `acceptance -> ppu -> hblank_ly_scx_timing-GS`       | ❌     |
| `acceptance -> ppu -> intr_1_2_timing-GS`            | ❌     |
| `acceptance -> ppu -> lcdon_timing-GS`               | ❌     |
| `acceptance -> ppu -> lcdon_write_timing-GS`         | ❌     |
| `acceptance -> ppu -> vblank_stat_intr-GS`           | ❌     |
| `acceptance -> serial -> boot_sclk_align-dmgABCmgb`  | ❌     |


#### GBC

| Test                                                 | Result |
| ---------------------------------------------------- | ------ |
| `misc -> bits -> unused_hwio-C`                      | ✅     |
| `misc -> boot_div-cgbABCDE`                          | ✅     |
| `misc -> boot_hwio-C`                                | ✅     |
| `misc -> boot_regs-cgb`                              | ✅     |
| `misc -> ppu -> vblank_stat_intr-C`                  | ❌     |