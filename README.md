# FMCW3 RF111 · 596 位首板候选 B

这份硬件适用于 5.0–5.5 GHz 的远距 FMCW 验证，一路发射、两路接收。六层板使用生益 S1000-2M 外侧 2116 叠层，板外形 103.960 × 69.965 mm。每板顶面 352 位、底面 244 位。两块装配合计 1192 件，归并 183 个订货标识。

| 文件 | 用途 |
| --- | --- |
| [KiCad 工程](hardware/fmcw3.kicad_pro) · [整套原理图](manufacturing/RF111_candidate_schematics_REVIEW_ONLY.pdf) | 用 KiCad 10.0.8 和随工程提供的符号、封装库打开 |
| [Gerber 和钻孔](manufacturing/gerbers) · [制造与装配说明](manufacturing/制造与装配说明.txt) | 按本批实际叠层、控阻及成品厚度回签 |
| [坐标](manufacturing/RF111_candidate_CPL_mm_REVIEW_ONLY.csv) · [逐孔工艺](manufacturing/RF111_candidate_hole_process_REVIEW_ONLY.csv) · [控阻图](manufacturing/RF111_candidate_impedance_locations_REVIEW_ONLY.pdf) | 同版双面贴装、193 个指定孔、L1/L6 控阻线定位 |
| [逐位物料](procurement/BOM_RF111_596_positions_B.csv) · [采购清单](procurement/RF111_candidate_purchase_sources_REVIEW_ONLY.csv) | 完整贴装型号、每板和两板净用量、供应商和可追溯目录 |
| [来源](SOURCE_CREDITS.txt) · [许可](LICENSE) · [逐文件校验](SHA256SUMS) | 上游归属与复现校验 |

B 版在原有焊盘上采用 R577/R579 5.1 Ω、R578 240 Ω 的本振匹配组合。U19 反馈电阻 R36/R37 分别取 102 kΩ 和 12.1 kΩ，Cff 为 390 pF。R310 和 R566 的完整订货号以逐位物料表为准。上电后先逐板校准检波，远距采集时锁定衰减器档位。两块工程样板使用同一套钢网、同批装配，首次带发射试验使用散热件、强制风冷及 50 Ω 负载。瞬态功率、接触温升及掉电恢复在首板核实后再合并正式分支。

本批 CAM 与贴装请配套使用[工艺复核说明](manufacturing/本批工艺确认.txt)、[裸板电测网表](manufacturing/ETest/RF111B_IPC-D-356A.d356)、[默认铜桥](manufacturing/RF111B_免采购位与默认铜桥.csv)和[方向坐标](manufacturing/RF111B_有方向元件辅助定位.csv)。每块板首次采集前按[USB 首次配置](hardware/USB首次配置.md)写入及读回 U32。当前 KiCad 最小通孔检查值为 0.250 mm。
