# zero-jev

Zero 的 Jev 研究与实验项目：研究如何把快速、类型化的语义判断用于浏览器、桌面自动化和应用工作流。

## 研究资料

- [Jev 使用研究与落地方案](docs/jev-usage-proposal.md)：模型原语、官方与社区协议差异、现有 MCP 审查、架构与评测方案。
- [Browser Use / Computer Use 项目清单](docs/browser-computer-use.md)：现有开源项目、选型建议与待验证项。

目前处于资料研究阶段，尚未完成候选项目的运行验证。

## 优先实验方向

1. Jev Browser：验证现成 MCP/CLI 的网页导航与信息获取。
2. PlayJev：验证 Playwright 确定性操作与 Jev 语义操作的组合。
3. Jev Ultrafast：研究 DOM 动作候选、并行提问和执行前状态检查。
4. typesafe-computer-use：研究 macOS OCR / Accessibility 驱动的桌面操作。

实验将比较任务成功率、端到端耗时、调用成本与失败原因。
