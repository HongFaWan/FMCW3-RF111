# RF111 B 首次 USB 配置

U33 为 FT2232HL-REEL。U32 为 93LC46BT-I/OT，组织方式 64 × 16。两块工程板各设一个基础串号，与板号和该板的校准记录对应。

先给单板限流供电，保持 PA 关闭，确认电源和 U33 复位已释放，通过 USB 使用 FT_PROG 读取并保存原配置。空白 EEPROM 允许芯片按默认身份枚举，后续采集使用同步 FIFO。

| FT_PROG 项目 | 本板设定 |
| --- | --- |
| USB VID / PID、产品描述 | 0403 / 6010，产品字符串 `fmcw3` |
| 序号 | 启用；两块分别写 `RF111001`、`RF111002`，D2XX 的通道名另带 A/B |
| 供电、挂起 | 自供电，关闭远程唤醒，启用 `Suspend_DBUS7`，U33.59 实际为 BCBUS7 / PWRSAV#，由 U690 的 VBUS 检测控制 |
| USB 总线取电声明 | 本板分压在 5 V 约取 0.34 mA。首板配置选 2 mA 并测量检查 |
| Port A、Port B | 两通道都选 245 FIFO、D2XX Direct |

每块完成写入后断开整板和 USB 电源，再连接并读回配置和串号。FPGA 的 FW101 校准镜像上电默认关闭发射。用 B 通道进行 JTAG 时先结束 A 的同步采集。使用 A 采集时，结束 B 的 JTAG 会话，按 D2XX `FT_SetBitMode(..., 0x40)` 切换同步 FIFO。确认两种 USB-C 插向均以高速枚举、U33.32 的 CLKOUT 与挑战帧 CRC 正确，并检查掉电重连及完整两通道采样。

[FTDI 双通道数据手册，第 32、46、52–56 页](https://ftdichip.com/wp-content/uploads/2024/03/DS_FT2232H.pdf) · [FT_PROG 手册](https://ftdichip.com/wp-content/uploads/2020/08/AN_124_User_Guide_For_FT_PROG.pdf)
