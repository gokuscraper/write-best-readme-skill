---
name: readme-writer
description: Use when 需要写、重写或更新 GitHub 项目 README、生成中英双语 README、捐赠文件(FUNDING.yml)或 MIT 协议(LICENSE)。触发词:写 README、生成项目文档、完善仓库首页、中英文 readme、赞助文件、开源协议。
---

# README Writer

## Overview

一次为 GitHub 仓库生成 4 份基础文件,让仓库首页专业、完整、有感染力:

1. `README.md` — 中文(默认)
2. `README_EN.md` — 英文(与中文互链,可一键切换)
3. `.github/FUNDING.yml` — 捐赠配置(GitHub 官方赞助按钮)
4. `LICENSE` — MIT 协议(项目无 LICENSE 时生成;已有则沿用)

**所有项目必须输出同一固定结构** —— 章节名、顺序、命名完全一致,只换内容。这是本 skill 的第一原则。

## 固定章节模板(必选/可选标注)

```
1. 居中头部:H1(生物emoji) + 斜体一句话简介 + 语言徽章与技术徽章并排一行 + Banner 占位区   [必选]
2. 简介段(可选,一两句铺垫定位)                                          [可选]
3. 为什么选它?(3-6 条差异化卖点,每条一句话)                             [必选]
4. 对比表(与同类工具/方案的功能矩阵)                                     [必选]
5. 安装 / 快速开始(推荐方式在前,可多选项)                               [必选]
6. 使用(真实命令 + 代码块;CLI 项目展示终端输出效果)                      [必选]
7. 工作原理 / 深度说明(有素材才放)                                       [可选]
8. Roadmap(存在 ROADMAP.md 才放,一行链接;无文件则整个跳过)              [可选]
9. 贡献与开发(指向 CONTRIBUTING.md/AGENTS.md)                          [必选]
10. 支持 / 捐赠(轻松语气 + 捐赠链接)                                     [必选]
11. License(一行链接,不复制全文)                                        [必选]
12. SEO Keywords(正文结束后的斜体关键词行)                               [必选]
```

**规则**:
- 第 4 条对比表是**必选**:扫描项目识别同类工具,输出功能矩阵表(含价格/开源/核心能力列)。拿不准竞品时,问用户;也允许与"手动/裸用方案"对比,但不能跳过
- 第 7、8 条可选节:素材不足就整节删除,其余章节顺序不动
- 中英两份 README 章节标题、顺序必须完全对应

## 风格基准

- **Mole 式生动**:H1 标题必须配一个「生物」emoji(见硬性规则);Support 捐赠段落语气轻松;CLI 项目用终端输出代码块展示效果
- **Mole 式居中头部**:
  ```html
  <div align="center">
    <h1>🐹 Mole</h1>
    <p><em>一句话简介,必须斜体。</em></p>
  </div>
  <p align="center">
    <a href="README.md"><img src="https://img.shields.io/badge/中文-blue?style=flat-square" alt="中文"></a>
    <a href="README_EN.md"><img src="https://img.shields.io/badge/English-gray?style=flat-square" alt="English"></a>
    <a href="LICENSE"><img src="https://img.shields.io/..." alt="License"></a>
    ...语言徽章 + 技术徽章全部并排一行,居中...
  </p>
  <!-- 📸 Banner 占位:徽章行之下预留 banner 位置(建议 1280×640),用 HTML 注释包一个示例
  <p align="center"><img src="assets/banner.png" alt="项目 banner"></p> -->
  ```
  语言徽章:当前语言高亮(blue),另一语言灰色(gray),排在徽章行最前,与其余徽章同一行
- **克制原则**:正文不过度使用 emoji;LICENSE/CONTRIBUTING/CHANGELOG 有独立文件,README 里只放一行链接,不整段复制

## 工作流

### 第 1 步:扫描项目

用 Read/Glob/Grep(或已有的项目信息)提取事实:
- 语言/框架/构建命令:看 package.json、pyproject.toml、go.mod、Cargo.toml 等 manifest
- 使用方式/CLI 命令:看 docs、src 入口、bin/ 脚本(不要复读现有 README,以代码为准)
- 已有文件:README.md / LICENSE / CONTRIBUTING / CHANGELOG / ROADMAP.md / .github/
- 截图/Logo:assets/、docs/**/*.png|jpg|gif

### 第 2 步:交互确认

拿不准的必须问,不猜。确认以下信息:
- 项目名与一句话简介(可含 emoji)、H1 生物 emoji 偏好
- 作者名(用于 LICENSE 署名)、当前年份
- 捐赠平台(默认 `ko_fi: gokuscraper` = https://ko-fi.com/gokuscraper,除非用户另给)
- 对比表竞品(扫描识别的同行,或用户指定)
- 若已有 README:哪些内容保留,哪些重写

### 第 3 步:生成 README.md(中文)

严格按上方固定章节模板输出,逐节填写。无素材节跳过,不写"待补充"。

**对比表示例样式**(Mole 风格):

| 功能 | Mole | CleanMyMac | AppCleaner | DaisyDisk | iStat Menus |
|------|:----:|:----------:|:----------:|:---------:|:-----------:|
| 清理 | ✅ | ✅ | ❌ | ❌ | ❌ |
| 免费开源 | ✅ | ❌ | ✅ | ❌ | ❌ |

**SEO Keywords 段样式**(Vecto 风格,8-15 个中英关键词):

```markdown
---

*Keywords: 关键词1, 关键词2, ..., keyword1, keyword2, ...*
```

### 第 4 步:生成其他文件

- **README_EN.md**:完整翻译,章节与中文完全对应;语言徽章互换高亮
- **FUNDING.yml**:
  ```yaml
  ko_fi: gokuscraper
  ```
  默认只写 ko_fi: gokuscraper;用户给了其他平台(GitHub Sponsors/custom)就加上,只留真实存在的
- **LICENSE**:项目已有 LICENSE 就保留并在 README 链接它;没有则用 MIT 标准文本,替换 `<year>` 为当前年份、`<copyright holders>` 为作者名

## 硬性规则

- **No fabrication**:所有命令、特性、数据必须来自真实项目或用户确认,禁止编造;扫描事实以代码/manifest 为准,不复读旧 README
- **生物 emoji 必须**:H1 标题必须配一个「生物」emoji —— 动物、植物或任何活物(🐹🐙🦋🪴…),禁止无生命 emoji(⚙️🎨📦🚀❌)。emoji 须贴合项目定位。交互确认时问用户偏好;用户不指定则由 agent 选最贴切的生物,不许跳过
- **结构统一**:所有项目 README 必须遵循同一固定章节模板,章节名/顺序/中英对应一致,不得自行增减或改名
- **对比表必须**:没有对比表不交付;竞品不明确就询问用户
- **已存在文件**:不盲目覆盖;README 已有内容先确认保留/重写,LICENSE 已存在则沿用
- **中英一致性**:两份 README 章节结构完全对应,内容等值翻译
- **发布检查清单**:发布/推送仓库前必须确认 `README.md` + `README_EN.md` + **banner 图已就位** + `.github/FUNDING.yml` + `LICENSE` 全部齐全;banner 用户未提供时,README 只能保留占位注释,并明确告知用户"待 banner 方可发布",不得擅自推送到远程
- **格式**:UTF-8 编码,GFM(GitHub Flavored Markdown)