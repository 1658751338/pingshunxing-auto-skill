# 平顺兴汽修 AI Skill

![Version](https://img.shields.io/badge/version-1.2.0-blue) ![License](https://img.shields.io/badge/license-MIT-green) ![Type](https://img.shields.io/badge/type-static-orange) ![Booking](https://img.shields.io/badge/booking-ai--powered-brightgreen)

这是一个 AI Skill——安装后，你的 AI 助手就能查询平顺兴汽修的信息：在哪修车、几点开门、保养多少钱、怎么叫救援、能不能上门取送车。现在还能**AI 对话预约**——告诉 AI 你的名字和车牌号，点开链接确认，师傅微信上就收到通知了。

临汾鼓楼南大街的汽修厂，现在有了自己的 AI 服务。

## 关于平顺兴

临汾市尧都区一家综合维修汽修厂，乘用车全车系通修。24 小时道路救援，支持上门取送车。

| 项目 | 内容 |
|---|---|
| 汽修厂名称 | 平顺兴汽修 |
| 经营类型 | 综合维修（乘用车全车系） |
| 地址 | 山西省临汾市尧都区鼓楼南大街 249 号 |
| 营业时间 | 早上 9:00 — 晚上 19:00 |
| 救援服务 | **24 小时**（全年无休） |
| 联系电话 | **15903571880**（微信同号） |

## 这个 Skill 能做什么

| 能力 | 你可以问 |
|---|---|
| 门店信息 | "平顺兴在哪？""几点开门？""电话多少？" |
| 保养服务 | "小保养多少钱？""有什么保养套餐？""该换变速箱油了" |
| 易损件更换 | "换刹车片多少钱？""电瓶该换了""火花塞要换了" |
| 养护清洗 | "节气门清洗多少钱？""空调有异味怎么办？" |
| 底盘维修 | "减震坏了""底盘异响" |
| 电路维修 | "故障灯亮了""车漏电" |
| 道路救援 | "车抛锚了""需要拖车""能搭电吗？" |
| 便民服务 | "能洗车吗？""做个全车检测" |
| 预约取送 | "怎么预约？""能上门取车吗？" |
| 🆕 AI 预约 | 告诉 AI 姓名+车牌号 → AI 生成链接 → 点开确认 → 师傅微信收到 |

## 目录结构

```
pingshunxing-auto-skill/
├── SKILL.md          # 核心文件：元数据 + AI Agent 指令 + 完整服务信息
├── skill.json        # 机器可读配置（工具定义、品牌设定）
├── booking.html      # 🆕 在线预约表单（PushPlus 推送到微信）
├── README.md         # 人类可读说明文档
└── LICENSE           # MIT 开源协议
```

## 安装

### 最简单的方式：告诉你的 AI 助手

直接拷贝下面这句话发给你的 AI 助手（Claude、Qoder、Cursor 等）：

> 帮我安装平顺兴汽修 Skill，仓库地址：https://github.com/1658751338/pingshunxing-auto-skill

Agent 会自动克隆仓库并安装到对应的 Skill 目录。

### 手动安装

将本仓库克隆到你 IDE 对应的 Skill 目录：

| IDE | Skill 目录 |
|---|---|
| Claude Code | `.claude/skills/pingshunxing-auto-skill/` |
| Qoder | `.qoder/skills/pingshunxing-auto-skill/` |
| Cursor | `.cursor/skills/pingshunxing-auto-skill/` |
| Trae | `.trae/skills/pingshunxing-auto-skill/` |
| Windsurf | `.windsurf/skills/pingshunxing-auto-skill/` |
| 通用 | `.agents/skills/pingshunxing-auto-skill/` |

```bash
# 示例：安装到 Claude Code
git clone https://github.com/1658751338/pingshunxing-auto-skill.git \
  .claude/skills/pingshunxing-auto-skill
```

只要目录下有 `SKILL.md`，Agent 下次启动就会自动加载这个 Skill。

## 版本说明

当前为 **静态版 v1.2.0**，所有信息以 SKILL.md 文档为准。

- ✅ 静态版：零成本、零服务器，AI 读取文档回答问题
- ✅ **AI 对话预约**：告诉 AI 姓名+车牌号 → 生成确认链接 → PushPlus 推送到微信
- 🔜 动态版（规划中）：对接 MCP 服务，支持实时查价

服务项目和价格如有调整，直接更新 SKILL.md 即可。

## 🆕 AI 对话预约

v1.2.0 预约方式升级——不再需要手动填表，跟 AI 说一声就行：

| 角色 | 体验 |
|---|---|
| 顾客 | 对 AI 说"预约保养，张三，晋A12345" → AI 生成链接 → 点开确认 |
| 师傅 | 微信收到 PushPlus 推送 → 查看姓名/车牌/服务 → 电话联系确认时间 |

**技术实现**：booking.html 支持 URL 参数（`?name=xxx&plate=xxx&service=xxx`），AI 负责拼装，用户确认后 PushPlus API 推送微信。

> 💡 也可以在微信/朋友圈直接分享预约链接：https://1658751338.github.io/pingshunxing-auto-skill/booking.html

## 给你的汽修厂也做一个？

欢迎 Fork 本仓库，把信息改成你自己的店就行。SKILL.md 里的信息填好，上传到 GitHub 或 Gitee，你的汽修厂就有了 AI 助手。

核心步骤：
1. 把店铺信息整理出来（地址、服务、价格、电话）
2. 把 SKILL.md 里的内容替换成你的
3. 注册 [PushPlus](https://www.pushplus.plus/) 获取 Token
4. 在 `booking.html` 中把 `PUSHPLUS_TOKEN` 换成你自己的 Token（约第 293 行）
5. 启用 GitHub Pages，顾客就能用你的专属链接在线预约

## License

[MIT](LICENSE)

---

📞 **平顺兴汽修** · 临汾市尧都区鼓楼南大街 249 号 · **15903571880** · 24 小时救援
