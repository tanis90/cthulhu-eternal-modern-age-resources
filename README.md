# Cthulhu Eternal — 现代纪元 SRD 中文译本

[Cthulhu Eternal](https://cthulhueternal.com/) 是 Cthulhu Reborn 发布的开源 d100 克苏鲁恐怖规则系统。
本仓库是 **Modern Age SRD v1.6**（107 页）的简体中文译本。

> **原文**：`originals/Cthulhu_Eternal_SRD-Modern_Age_v1_6.pdf`
> **许可**：Open Game License 1.0a。OGL 在 "Derivative Material" 的定义中**明确包含 translations**，
> 因此本译本为合法衍生作品，同样以 OGL 1.0a 发布。许可原文见 [译文/99-许可.md](译文/99-许可.md)。
> **Open Content 范围**：除 "Cthulhu Eternal" 名称与 Logo 外，全部正文、表格、角色卡均为开放内容
> （见 SRD 末页 Product Identity 声明）。

## 规模

| 项 | 值 |
|---|---|
| 原文 | 107 页，266,308 字符 |
| 翻译单元 | 89 节 |
| 译文 | 114,309 字 |
| 完成率 | 89/89，零失败 |
| 耗时 | 2,846 秒（并发 4） |
| Token | 输入 253,067 / 输出 112,492 |
| 术语违规 | **0** |
| 中位压缩比 | 0.374（英→中正常区间） |

## 结构

```
originals/      原始 PDF
原文/           MinerU 解析 + 按章切分的 Obsidian 笔记
译文/           分节译文 + 合并稿 + 校对报告
glossary/       译名对照表（Cthulhu Eternal 术语体系）
assets/images/  原书插图
tools/          fix_ocr / split / translate / qa
raw/            MinerU 原始输出（不提交）
```

## 与 CoC 的关键差异

这套系统**不是** CoC 7e 的中译，术语不能照搬：

| | Call of Cthulhu 7e | Cthulhu Eternal |
|---|---|---|
| 玩家角色 | Investigator 调查员 | **Protagonist 主角** |
| 主持人 | Keeper 守秘人 | **Game Moderator 主持人** |
| 属性 | 8 项（含 SIZ/EDU/APP） | **6 项**（STR/CON/DEX/INT/POW/CHA） |
| 理智 | SAN | SAN（同）但多 **Breaking Point 崩溃点** |
| 关系 | 无 | **Bonds 羁绊** |
| 技能数 | 50+ | **42** |

完整对照见 [glossary/译名对照表.md](glossary/译名对照表.md)。

## 流程

见 `~/.kimi-code/skills/trpg-translation/SKILL.md`。本仓库用的命令：

```bash
mineru-open-api extract originals/...pdf --language en -f md,json -o raw/
python3 tools/fix_ocr.py <pdf> raw/main.md raw/clean.md      # 修 OCR 丢空格/连字
python3 tools/split.py raw/clean.md . --title "Cthulhu Eternal: 现代纪元 SRD"
python3 tools/translate.py . --glossary glossary/译名对照表.md --model mimo-v2.6-flash
python3 tools/qa.py . --glossary glossary/译名对照表.md
```

## 校对说明

- 术语零违规：主角、主持人、羁绊、资源、逆境技能、崩溃点、致命等级、六属性、42 项技能全部按表执行
- 长度比检查：逐节比对去标记后的中英字符数，最低 0.32、中位 0.374，无截断
- 标题层级：模型把 `## 2.8.1` 这类子标题降级为 `###`，比原文的平铺结构更符合实际层级，**判为改进，保留**
- OGL 正文保留英文，未翻译

## 许可

- 原文与译文：Open Game License 1.0a
- 脚本：MIT
- "Cthulhu Eternal" 名称与 Logo 为 Cthulhu Reborn Publishing 商标，不在开放内容范围内
