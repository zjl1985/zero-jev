# Jev 浏览器与桌面自动化项目

核对日期：2026-09-21。以下基于项目原始仓库，尚未本地运行。推荐顺序属于本项目的选型判断，不代表生产稳定性认证。

| 项目 | 提供什么 | 适合的用途 | 已知边界 |
| --- | --- | --- | --- |
| [jkudish/jev-browser](https://github.com/jkudish/jev-browser) | MCP、CLI、JS 库；任务驱动浏览器，输出轨迹、页面和截图 | 最先体验完整流程 | 早期软件；复杂交互、iframe、Shadow DOM 等仍有限制 |
| [filedcom/playjev](https://github.com/filedcom/playjev) | 包装 Playwright page，增加自然语言 act 和语义 check | 融入 Node/TypeScript 自动化代码 | 明确为实验项目；要求 Chromium/CDP |
| [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) | Jev 选择操作与 DOM 元素，生成模型负责输入文字；带本地调试界面 | 研究快速决策循环 | MVP 不支持所有网页控件；云端候补名单与本地开源项目要区分 |
| [awlevin/typesafe-computer-use](https://github.com/awlevin/typesafe-computer-use) | 本地 OCR 与 Accessibility 提供控件，Jev 决策，macOS 执行 | 跨原生应用操作研究 | macOS 14+；需要屏幕录制和辅助功能权限；可先 dry-run |

## 共通架构

```text
DOM / OCR / Accessibility
    → 带 ID 的可操作控件
    → Jev 从受限候选中选择操作和目标
    → 驱动执行
    → 重新观察
```

Jev 在这些项目里消费文字/结构化状态，不直接承担截图视觉理解。需要自由输入文本时，可由生成模型补充。项目实现见 [Ultrafast 动作空间](https://github.com/browser-use/jev-ultrafast#the-action-space) 与 [桌面循环](https://github.com/awlevin/typesafe-computer-use#how-a-step-works)。

## 如何判断是否值得用

先比较同一组实际任务：打开目标页面、搜索并进入指定结果、填写但不提交表单、选择筛选项并确认结果。成功条件用 URL、DOM 字段或独立断言检查，不能只相信模型返回 done。

每次保存：固定源码版本、实际模型、任务、成功/失败、总耗时、模型耗时、步骤数、输入 tokens、生成模型费用、失败轨迹。再扩展到中文页面、动态布局和复杂表单。

Ultrafast 的约 7 秒航班搜索是作者的小规模任务实验，计时不含初始导航与事后独立验证，不能外推为通用性能。[原始性能报告](https://github.com/browser-use/jev-ultrafast/blob/main/docs/performance.md)

## 更多项目

[hellogumbo/awesome-jev](https://github.com/hellogumbo/awesome-jev#browser--computer-use) 可用于发现候选；它是社区目录，最终仍应回到原始仓库核对代码、依赖和限制。
