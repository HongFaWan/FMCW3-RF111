# FMCW3 RF111B · 619 位工程首板

这版六层主板用于 5.0–5.5 GHz 固定远距档 FMCW 验证，含一路发射和两路接收。每片实装 619 位，顶面 362 位、底面 257 位，共 198 个订货号。装配文件按一片计数。

| 用途 | 文件 |
| --- | --- |
| 查看和修改电路 | [KiCad 工程](hardware/fmcw3.kicad_pro) · [17 页原理图 PDF](manufacturing/RF111B_619_schematics.pdf) · [PCB](hardware/fmcw3.kicad_pcb) |
| 制板与电测 | [Gerber 和钻孔](manufacturing/gerbers) · [IPC-D-356A 裸板电测网表](manufacturing/ETest/RF111B_IPC-D-356A.d356) · [分层阻抗线路图](manufacturing/RF111B_619_impedance.pdf) |
| 逐孔工艺 | [30 处指定填孔盖铜](manufacturing/03A_必须填盖孔.csv) · [163 处开孔或条件复核](manufacturing/03B_开孔和条件复核.csv) · [制造与装配说明](manufacturing/制造与装配说明.md) |
| 贴片与装配核对 | [双面贴装坐标](manufacturing/RF111B_619_CPL_mm.csv) · [有方向元件定位](manufacturing/RF111B_有方向元件辅助定位.csv) · [免采购位与默认铜桥](manufacturing/RF111B_免采购位与默认铜桥.csv) |
| 采购 | [619 位逐件 BOM](procurement/BOM_RF111B_619.csv) · [198 组订货号、备选和采购渠道](procurement/RF111B_198_采购渠道.csv) |
| 上电与版本核对 | [USB 首次配置](hardware/USB首次配置.md) · [逐文件 SHA-256](SHA256SUMS) · [上游归属](SOURCE_CREDITS.txt) · [许可](LICENSE) |

用 KiCad 10.0.8 打开工程并保留 `hardware/libraries` 的相对位置。采购表的数量为单板净用量，起订量和贴装损耗按选用供应商另计。淘宝店铺及商品标题只在原号或已核包装号相符时列出。下单时核对完整型号、包装、批次及实际可交付数量。

## 首板上电

对应固件为 **FW101-619R2**。首次限流上电用 `RF111B_619_FW101_bringup.bit`，该镜像将 PA_EN 保持为低。混频器和采集在使能条件稳定后共等待 409.6 µs。临时标定用 `RF111B_619_CAL_JTAG_ONLY.bit`。每片的工作镜像使用该板的实测标定数据生成。

| 对象 | SHA-256 |
| --- | --- |
| 本版 PCB | `a31ce20355b4fa4a97ab1be27c61c8bd2aee6932014cd293fbca63f2d87f8769` |
| 首板上电 .bit | `9f23ade9e8424474dfdef7c0eb7f3b96057b2d42a69f1a3f6b118c192e5e65d3` |
| JTAG 标定 .bit | `038ec09d5bfff4f78416c5b02aa63c316596a4f46cf53e25bf58e2a450170f9a` |

当前分支用于首板打样。合并主分支前，需在实板核实固定档本振两端余量、PA 与 U22 装壳温升、U29 冷启动及掉电恢复，并完成双通道回波采集。
