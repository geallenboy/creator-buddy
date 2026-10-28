# Creator Buddy（gegarron 个人版）

<p align="center"><code>creator-buddy.skill</code></p>

<p align="center"><em>把学习笔记 / 口播，做成能发的短视频</em></p>

<p align="center">
  <img alt="License MIT" src="https://img.shields.io/badge/License-MIT-c8a500?style=for-the-badge">
  <img alt="Agent Skills Standard" src="https://img.shields.io/badge/Agent%20Skills-Standard-5aa524?style=for-the-badge">
  <img alt="skills.sh Compatible" src="https://img.shields.io/badge/skills.sh-Compatible-1888c8?style=for-the-badge">
</p>

**定位**：给 [gegarron](https://gegarron.com) 自己用的 Agent Skill 箱——把学习笔记、口播素材做成**能发的短视频成品**。  
**不做**：代发任何平台、账号运营自动化、一键起号。

- **主阵地**：个人网站 [gegarron.com](https://gegarron.com) / [docs.gegarron.com](https://docs.gegarron.com) + X  
- **文字稿流水线**：另有「AI自媒体」Bot 负责；本仓库默认主线是**视频 Skills**  
- **基于**：[SpaceZephyr/creator-buddy](https://github.com/SpaceZephyr/creator-buddy)（MIT）二次开发的薄换皮；原作者权利见 [`LICENSE`](./LICENSE) / [`NOTICE`](./NOTICE)

---

## 默认主线：视频 · `video-Skills`

一条视频从想法到成片，由 `space-video` 总控调度。

### P0 推荐最小闭环（先跑通再加料）

```text
space-video  →  space-video-edit  →  space-video-subtitle
   总控/导演        剪口误（删前保后）      转写 · 断句 · SRT
```

P0 **暂不加** B-roll / 配乐；成片够发再说。

| Skill | 干什么 | P0 |
|---|---|---|
| `space-video` | **总控/导演**：判断走哪步、路由子技能、成片后复盘 | ✅ |
| `space-video-edit` | 剪辑：剪口播（删前保后 + 风险分层）+ 成片 | ✅ |
| `space-video-subtitle` | 字幕：转写 · 断句 · AI 校对 · 烧录 / 出 SRT | ✅ |
| `space-video-topic` | 选题：下载参考去水印 · 逐字稿 · 标题 · 正文 | 可选 |
| `space-video-transcript` | 链接转字幕：YouTube/小宇宙/B站/抖音/小红书 → Markdown + SRT | 可选 |
| `space-video-script` | 脚本：去 AI 味口播 + 精确到秒分镜 | 可选 |
| `space-video-broll` | B-roll：HTML→确定性 MP4 | 非 P0 |
| `space-video-broll-sketch` | B-roll：文章转手绘图解 | 非 P0 |
| `space-video-audio` | 配音配乐：TTS · BGM · 混音 | 非 P0 |
| `space-video-cover` | 封面：平台比例缩略图 | 可选 |

---

## 非主线（保留，按需用）

公众号 / 小红书目录**完整保留**，但不作为本 fork 的默认主线。文字成稿优先走「AI自媒体」Bot；需要平台情报或排版时再进下面的 Skill。

```text
gzh-Skills/     公众号   ── 非主线：定位 · 搜爆款 · 写长短文 · 标题 · 封面配图 · 排版
xhs-Skills/     小红书   ── 非主线：定位 · 选题 · 标题 · 正文 · 封面 · 图文 · 复盘
video-Skills/   视频     ── ★ 默认主线
```

### 📰 公众号 · `gzh-Skills`（非主线）

| Skill | 干什么 |
|---|---|
| `gzh-positioning` | 账号简介 / 关注后回复 / 菜单三件套 |
| `gzh-longform-writer` | 长文：六种写法路由 + 成稿质检 |
| `gzh-short-post` | 短文：≤1000 字纯文字推送 |
| `baokuan-article-analysis` | 按赛道/关键词抓公众号爆款 |
| `gzh-explosive-content-detector` | 每日爆款收录 |
| `global-content-search` | 全域内容搜索（小红书/B站/抖音） |
| `baokuan-title-generator` | 科技/AI 爆款标题生成、评分、A/B |
| `space-gzh-cover` | 2.35:1 头图 |
| `space-chart-image` | 10 类图表配图 |
| `space-text-logic-diagram` | 文本逻辑拆解 → 关系图 |
| `space-wechat-layout` | 整篇文章 → 公众号 HTML |

### 📕 小红书 · `xhs-Skills`（非主线）

| Skill | 干什么 |
|---|---|
| `space-xhs-buddy` | 总控台：判断卡点、路由工作流 |
| `space-xhs-positioning` | 起号定位 |
| `space-xhs-hotspot` | 热点选题 |
| `space-xhs-title` | 爆款标题 |
| `space-xhs-writer` | 笔记正文 |
| `space-xhs-cover` | 封面 3:4 |
| `xhs-html` | 图文排版 HTML |
| `space-xhs-image` | AI 信息图 |
| `space-xhs-account-audit` | 账号体检 |
| `space-xhs-note-analytics` | 笔记复盘 |

---

## 安装

基于开放的 Agent Skills 协议，可在 Claude Code、Codex、Cursor 等兼容 runtime 中运行。

### 方式一：一行命令（推荐）

```bash
npx skills add geallenboy/creator-buddy
```

需要指定 runtime 时加 `-a codex` / `-a claude-code` / `-a cursor`。

或告诉 agent：

```text
帮我安装这个 skill：https://github.com/geallenboy/creator-buddy
```

### 方式二：手动安装

```bash
git clone https://github.com/geallenboy/creator-buddy.git
```

把需要的 skill 目录复制到你的 runtime skills 目录。每个子目录是一份独立 `SKILL.md`（+ 可选脚本/references）。

### 方式三：当参考资料

直接打开对应目录的 `SKILL.md`，粘贴进对话即可。

---

## 使用（P0 视频闭环示例）

```text
用 space-video 帮我把这段口播做成能发的短视频
先剪口误，再出 SRT 字幕；先不要 B-roll 和配乐
```

其他仍可用的自然语言（非主线）：

```text
帮我搜一下小红书最近 Codex 的热门笔记
查一下公众号里 AI Agent 相关爆款
把这个 YouTube / 小宇宙 / B站链接提取成字幕
```

---

## 风控与诚实边界

本 fork 继承上游定位：**公开内容研究与创作辅助，不是账号自动化工具**。

- **不代发**：不发帖、点赞、收藏、评论、关注、私信。
- **不绕过限制**：不绕登录、验证码、付费墙、平台风控。
- **凭据不入库**：API Key、Cookie、登录态、`.env` 都不提交。
- **热门 ≠ 适合你**：爆款只说明平台在传播什么，不能替代定位判断。
- **AI 出图/成片有上限**：交付前需人工检查。

---

## 参考与致谢

本仓库基于 [SpaceZephyr/creator-buddy](https://github.com/SpaceZephyr/creator-buddy)（MIT）。上游 README 列出的主要参考：

- [Agent Reach](https://github.com/Panniantong/Agent-Reach)
- [xiaohongshu-openclaw-skill](https://github.com/um-why/xiaohongshu-openclaw-skill)
- [SpaceZephyr/design-buddy](https://github.com/SpaceZephyr/design-buddy)
- [HyperFrames](https://github.com/heygen-com/hyperframes)
- 火山引擎 **Seedance 2.0**（火山方舟 Ark）与 **libtv Agent**
- Pluviobyte/rnskill 与 chengfeng-videocut（口播剪辑方法论）

详见 [`NOTICE`](./NOTICE)。

## 许可证

[MIT](./LICENSE)
