<div align="center">

# ONEPERCENT

**风险优先的行情终端，仅一个 `index.html` 文件**

**语言：** [English](README.md) | [Deutsch](README.de.md) | **中文** | [Dansk](README.da.md)

[在线演示](https://kbgirishhb.github.io/Onepercentage/) | [用户指南](docs/USER_GUIDE.md) | [部署](docs/DEPLOYMENT.md) | [架构](docs/ARCHITECTURE.md)

</div>

---

## 为什么有 ONEPERCENT

大多数交易应用只显示价格，几乎不会要求你在冲动之前先确定**仓位大小、止损位和退出计划**。ONEPERCENT 从风险出发：**1% 规则**是核心。

> **我到底买什么、买多少、在哪里认错、何时带着利润离场？**

## 功能

- **实时行情：** 股票、ETF、指数、印度股票（`.NS`）和加密货币，无需 API 密钥，多级备用数据源
- **自制 K 线图：** 7 个时间周期，缩放、拖动、十字光标、成交量
- **指标：** EMA20/50、VWAP、布林带、成交量，以及 RSI 和 ATR 的通俗解读
- **1% 风险引擎：** 每日风险表盘（硬性上限）、仓位计算器、仓位占比上限、含手续费的盈亏平衡价
- **截图并分析：** 一键切换到 1 分钟图，生成计划并评估盈亏比
- **截图分析器：** 粘贴券商截图，拖动三条线，得到 TAKE、MARGINAL 或 REJECT（低于 2R 一律拒绝）
- **退出计划：** Sniper、分批止盈、时间止损、ATR 追踪
- **交易日志：** 以 R 倍数记录，仅保存在本机
- **我的计划：** IST 与美东时钟、交易时段、4 个问题生成个人计划
- **美元 / 卢比：** 按实时汇率一键切换
- **诚实的数据标记：** `LIVE`、`GH - DELAYED`、`CACHED`、`SIMULATED`

## 1% 计算示例

```text
账户 8,000 -> 每日风险 80（1%）
止损距离 0.20 -> 数量 = 80 / 0.20 = 400 股
触发止损时恰好亏损 1%
```

## 部署（免费）

1. 创建公开仓库并上传 `index.html`
2. Settings > Pages > Deploy from a branch > `main` / (root)
3. 完成：https://kbgirishhb.github.io/Onepercentage/

获取真实行情请参见 [DEPLOYMENT.md](docs/DEPLOYMENT.md)（GitHub Action、Cloudflare Worker、Finnhub；文档为英文）。

## 免责声明

ONEPERCENT 是**教育工具**，不构成投资建议。数据可能延迟或为模拟数据。请务必在券商处核实价格。交易存在重大亏损风险。

## 许可证

[MIT](LICENSE.txt)
