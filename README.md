<div align="center">
  <h1>🦉 write-best-readme-skill</h1>
  <p><em>给 AI Agent 用的 README 生成技能:中英双语、结构统一、对比表必选,一次配齐 4 份文件。</em></p>
</div>

<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/中文-blue?style=flat-square" alt="中文"></a>
  <a href="README_EN.md"><img src="https://img.shields.io/badge/English-gray?style=flat-square" alt="English"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/gokuscraper/write-best-readme-skill?style=flat-square" alt="License"></a>
  <a href="https://github.com/gokuscraper/write-best-readme-skill/stargazers"><img src="https://img.shields.io/github/stars/gokuscraper/write-best-readme-skill?style=flat-square" alt="Stars"></a>
  <a href="SKILL.md"><img src="https://img.shields.io/badge/Agent_Skill-ready-8A2BE2?style=flat-square" alt="Agent Skill"></a>
  <img src="https://img.shields.io/badge/Markdown-000000?style=flat-square&logo=markdown" alt="Markdown">
</p>

<p align="center">
  <img src="assets/banner.png" alt="write-best-readme-skill banner">
</p>

write-best-readme-skill(技能名 `readme-writer`)是一个给 Claude Code、opencode 等 AI Agent 加载的**技能(Agent Skill)**:扫描真实项目代码,一次生成 `README.md`(中文)、`README_EN.md`(英文)、`.github/FUNDING.yml`、`LICENSE` 四份文件,让**每一个项目的 README 都长成同一个模子**——章节骨架固定、双语结构一一对应,从"为什么选它"到对比表再到 SEO Keywords,一个都不缺。

## 为什么选 write-best-readme-skill?

- **所有项目共用一套骨架**:固定 12 节章节模板(为什么选 → 对比表 → 安装 → 使用 → 工作原理 → Roadmap → 贡献与开发 → 支持 → License → SEO Keywords),项目间不再风格分裂,看起来像同一个团队维护
- **对比表必选**:没有对比不交付;竞品不明确就问,不许跳过——读者一眼看出你和其他方案差在哪
- **中英双语一次配齐**:`README.md` + `README_EN.md` 章节完全对应,语言徽章在当前行内互切,英文版不是敷衍机翻
- **发布零遗憾**:banner 位置预留、FUNDING.yml、LICENSE 一次生成;素材不齐(缺 banner 等)明确告知"待补齐方可发布",不擅自推送
- **No fabrication**:所有命令、特性、数据只来自真实项目代码或用户确认,禁止编造、禁止复读旧 README
- **有性格、不无聊**:H1 强制配「生物」emoji(🐹🦋🦉…),CLI 项目直接展示终端输出,支持段语气轻松
- **对 Agent 友好**:SKILL.md 里写明完整工作流与硬性规则,任何 Agent 加载后都能稳定产出同款结果

## 对比

| 能力 | write-best-readme-skill | general-readme-skill | awesome-copilot readme | readme-ai |
|------|:---:|:---:|:---:|:---:|
| 形态 | Agent Skill | Agent Skill | Agent Skill | CLI 工具 |
| 中英双语配套(结构对应) | ✅ | ❌ | ❌ | ❌ |
| 项目间统一章节模板 | ✅ | ❌ | ❌ | ❌ |
| 对比表强制 | ✅ | ❌ | ❌ | ❌ |
| 配套 FUNDING.yml + LICENSE | ✅ | ❌ | ❌ | ❌ |
| Banner 位预留 | ✅ | ❌ | ❌ | ❌ |
| 事实只来自代码(No fabrication) | ✅ | 视模型 | ❌(仅引用示例) | 视模型 |
| 价格 | 免费开源 | 免费开源 | 免费开源 | 免费开源 |

> 对比基于各仓库公开页面的快照,功能可能随版本变化,以各自仓库为准。

## 安装

```bash
# 方式一:克隆仓库,使用其中的 skill 目录
git clone https://github.com/gokuscraper/write-best-readme-skill.git

# 方式二:只复制 readme-writer 目录到你的 Agent skill 目录
cp -r write-best-readme-skill/readme-writer <skill 目录>/
```

常见 skill 目录:`~/.claude/skills/`(Claude Code)、`.agents/skills/`(opencode 项目级)、`~/.config/opencode/skills/`(opencode 全局)。

## 使用

对 Agent 说这些触发词即可:写 README、生成项目文档、完善仓库首页、中英文 readme、赞助文件、开源协议。

Agent 会按 4 步工作流执行:

1. **扫描项目**:读 manifest、CLI 入口、docs、已有文件(以代码为准,不复读现有 README)
2. **交互确认**:项目名/一句话简介/生物 emoji 偏好、作者名与年份、捐赠平台(默认 `ko_fi: gokuscraper`)、对比表竞品
3. **生成 README.md(中文)**:按 12 节固定模板逐节填写
4. **生成配套文件**:README_EN.md(对应翻译)、FUNDING.yml、LICENSE(MIT 或沿用已有)

产物四件套:

| 文件 | 说明 |
|------|------|
| `README.md` | 中文版,固定 12 节模板,含 SEO Keywords 段 |
| `README_EN.md` | 英文版,章节与中文完全对应,语言徽章互切 |
| `.github/FUNDING.yml` | 赞助配置,默认 `ko_fi: gokuscraper` |
| `LICENSE` | MIT(项目没有时生成),或沿用项目已有协议 |

## 工作原理

固定章节模板(必选/可选):

```
1. 居中头部(H1 生物emoji + 斜体一句话 + 徽章行 + Banner 占位)   [必选]
2. 简介段                                                      [可选]
3. 为什么选它?(3-6 条差异化卖点)                               [必选]
4. 对比表(同类工具功能矩阵)                                    [必选]
5. 安装 / 快速开始                                             [必选]
6. 使用(真实命令 + 代码块;CLI 展示终端输出)                     [必选]
7. 工作原理 / 深度说明                                         [可选]
8. Roadmap(有 ROADMAP.md 才放一行链接)                         [可选]
9. 贡献与开发                                                  [必选]
10. 支持 / 捐赠                                                [必选]
11. License(一行链接)                                         [必选]
12. SEO Keywords(斜体关键词行,中英各一份)                      [必选]
```

核心机制在 [`SKILL.md`](SKILL.md):工作流 + 硬性规则(No fabrication、生物 emoji 必须、对比表必须、结构统一、发布检查清单、中英一致性)。

## 贡献与开发

拿任意真实项目跑一遍 `write-best-readme-skill`,产出后对照 12 节模板自查:

- ✅ 章节顺序、命名与模板完全一致
- ✅ 对比表存在且多数数据可追溯到项目代码
- ✅ 中英两份章节一一对应
- ✅ H1 有生物 emoji,一句话简介为斜体
- ✅ 尾部有 SEO Keywords 段
- ✅ banner 位已预留(占位注释)

规则修改请直接改 `SKILL.md`,并在下方硬性规则一节同步说明。欢迎提交 PR。

## 支持

如果这个技能帮到了你,请我喝杯咖啡 ☕ [ko-fi](https://ko-fi.com/gokuscraper)——每一份支持都让维护者更有动力。

## License

[MIT](LICENSE) © gokuscraper。

---

*Keywords: readme 技能, 生成 readme, 中英双语 readme, github 项目文档, agent skill, claude code skill, opencode skill, readme 模板, 对比表, 开源项目文档, 捐赠文件, readme skill, bilingual readme, github readme generator, agent skill, readme template, comparison table, open source documentation, fund.yml, license generator*