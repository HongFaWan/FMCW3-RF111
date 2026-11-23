# FMCW3 RF111 · 0.250 mm 钻孔候选

此分支记录 2026-11-23 的独立工程候选，源自 RF111 主分支。首批目标为 5 片六层板、其中 2 片双面装配。工厂回签和功能验证通过后再合并。当前 Gerber 和装配表仅供审图询价。

| 资料 | 入口 |
| --- | --- |
| KiCad 10 项目、原理图、PCB 和本地库 | [KiCad 项目](hardware/fmcw3.kicad_pro) |
| 各层级原理图 | [原理图 PDF](manufacturing/RF111_candidate_schematics_REVIEW_ONLY.pdf) |
| 6 层铜、双面加工数据和钻孔 | [Gerber 与 Excellon](manufacturing/gerbers) |
| 装配坐标和关键工艺 | [CPL](manufacturing/RF111_candidate_CPL_mm_REVIEW_ONLY.csv) · [填孔和开孔](manufacturing/RF111_candidate_hole_process_REVIEW_ONLY.csv) · [阻抗标注](manufacturing/RF111_candidate_impedance_locations_REVIEW_ONLY.pdf) · [工艺说明](manufacturing/制造与装配说明.txt) |
| 204 组候选物料与可追溯来源 | [BOM](procurement/BOM_RF111_candidate_204groups_REVIEW_ONLY.csv) · [采购来源及待核状态](procurement/RF111_candidate_purchase_sources_REVIEW_ONLY.csv) |
| 上游归属、许可和文件校验 | [来源](SOURCE_CREDITS.txt) · [GPL v3](LICENSE) · [SHA-256](SHA256SUMS) |

## 复现

克隆后在 KiCad 10.0.8 打开硬件项目。库表使用项目相对路径。封装和符号可在项目内解析，部分标准封装的 3D 显示使用 KiCad 自带模型。PCB 保留送厂审图时的原始字节。Gerber、钻孔、BOM、CPL 和工艺表须取自同一候选版本。

这版包含独立本振、检波、PA 联锁、输入 eFuse 和 RF5V 电源回路。最小金属化 CAD 钻孔为 0.250 mm。每板 578 个装配位置，顶面 335、底面 243，两板净用量 1156 件。BOM 中 49 组仍待确认原厂完整型号，采购来源有单独状态。固件和外置模块另行管理。

## 合并前检查

- 取得实际生产叠层和阻抗、钻孔公差及最低孔铜、填孔盖铜、三处 SMA 试插、钢网和检验回签。
- 用最终叠层核对 RF 路径和 PA 泄漏，验证所有温度和换档工况下的本振上下限余量。
- 确认 U14/U22 散热、供电和掉电联锁、热插拔、USB 复位及采集恢复，并关闭影响首板的装配警告和关键采购缺项。
