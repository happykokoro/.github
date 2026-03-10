# $67K 本金做到 $113 万：拆解一个 Polymarket 做市 Bot 的 3,379 笔交易

**Author:** Leo (@runes_leo)
**Source:** https://x.com/runes_leo/status/2030968488341430556
**Date:** Mar 9, 2026
**Stats:** 7 replies · 19 reposts · 94 likes · 13K views

![Header Image: Blue gradient banner](screenshot-header)

![Article includes: 交易频率热力图 (Trading frequency heatmap)](screenshot-heatmap)
![Article includes: 1h入场时间双峰分布图 (1h entry time bimodal distribution chart)](screenshot-bimodal)
![Article includes: 各币种做市盈亏表 (PnL table by coin)](screenshot-pnl-table)
![Article includes: 各时间框架做市表现 (Performance by timeframe)](screenshot-timeframe)
![Article includes: PnL翻正过程 (PnL recovery chart)](screenshot-pnl-recovery)
![Article includes: 信号来源验证 (Signal source verification)](screenshot-signal)
![Article includes: Bilateral做市机制示意图 (Bilateral market-making mechanism diagram)](screenshot-mechanism)
![Article includes: Bot 活跃期 vs 现在 (Bot active period vs now)](screenshot-bot-status)

---

Polymarket 上有一类地址，不赌方向、不抄别人，每分钟下 34 单，24/7 不停。累计盈利超过 $113 万。

我拉了它高峰期 100 分钟内的 3,379 笔交易做拆解，看看一个专业做市 Bot 到底在干什么，怎么赚钱，又怎么亏钱。你可以直接查看这个 Bot 的主页，对照着读。

## Bot 基本面

这个地址（0x1979...7c9d）在高峰期同时维护 100 个 position，覆盖 BTC、ETH、SOL、XRP 四个币种，横跨 5 分钟到 4 小时四个时间框架。

总部署资金约 $67,000。

最关键的特征：100% 是 BUY 订单，0% SELL。

等等，只买不卖怎么赚钱？后面解释。

## 交易频率：不是在下单，是在"刷墙"

100 分钟内 3,379 笔交易，平均每分钟 34 笔。

几个直观的发现：

- ETH 1h 是绝对主力（737 笔），单一品种贡献最大交易量
- BTC 15m 次之（595 笔），高频维护
- XRP 5m 完全空白（0 笔），说明 Bot 会根据流动性选择性放弃
- 同一个 10 秒窗口内，经常 3-4 个时间框架同时有交易在跑

这不是"看到信号下单"的交易者行为，是全时段维护订单簿的做市行为。

## 入场时间：双峰分布暴露做市逻辑

如果是信号驱动的交易者，入场时间应该是随机的。但这个 Bot 的 1 小时市场入场时间分布长这样：

两个明显的峰值：

- **开盘 0-10%：11.6%**（抢 queue priority，排在订单簿前面）
- **收盘 90-100%：15.6%**（在 candle 结算前刷新订单）

中间段均匀分布在 7-8.5%。

4h 市场更极端：36% 的交易集中在开盘前 10%。

做市商的核心竞争力不是"预测得准"，是"排得前"。

## 赚钱的币和亏钱的币

不是所有品种都赚钱。

BTC 是做市的雷区。单个 1h candle 就亏了 $1,988，因为 position size 太大（20,138 shares），BTC 剧烈波动时 adverse selection 直接吃掉利润。

时间框架也有明显差异：

4h 是利润率最高的时间框架，100% 盈利。但交易频率只占 5.7%。

做市的矛盾在这里：频率越高竞争越激烈，频率低了又吃不到量。

## 做市不是无风险的

很多人以为做市是"稳赚不赔"。数据说不是。

2 月 21 日晚间，BTC 1h 大波动，Bot 整体 PnL 从正转负到 -$960。

但到第二天早上，PnL 翻正到 +$947。

这就是做市的"自愈能力"：只要价差结构没有永久性破坏，后续 candle 的正常价差利润会逐步覆盖前面的大亏。

前提是——你扛得住那个 drawdown。

## 它不是纯做市：方向信号发现

深挖数据后发现一个有趣的事：Bot 不是纯粹的双边做市，它实时跟踪 Binance 价格来调整 Up/Down 的买入比例。

我逐分钟对比了 Bot 的 Up/Down 买入量和 Binance 价格变化，排除了几个假设：

Bot 使用微观价格信号（Binance 实时价格 vs candle open），而不是趋势跟随。

验证数据：
- 方向匹配率 74%
- 方向准确率 77%
- 买贵侧比例 100%（总是买它认为会赢的那边多一点）
- 逆 1h 动量 71%，但顺 15m 动量 74%

这意味着它在纯做市之上叠加了方向判断。"买贵"不是 adverse selection 的结果，是主动选择。

但这也解释了它在 BTC 大波动时为什么亏更多：方向判断错误 x 偏置放大 = 更大的单边暴露。

想观察 Polymarket 上 Crypto Up or Down 市场的实时数据？搜 "BTC 1 hour" 就能看到这类做市 Bot 活跃的市场结构。

## 做市机制：为什么 100% 是 BUY

Polymarket 上每个市场有 UP（YES）和 DOWN（NO）两个 token。

做市商同时买两边：

- 买 UP $0.48 + 买 DOWN $0.48 = 成本 $0.96
- 不管涨跌，赢的那边兑付 $1.00
- 每对利润 = $1.00 - $0.96 = $0.04

所以交易记录里 100% 是 BUY——因为两边都在买，赚的是中间 4 美分的价差。

三个额外优势：

- **Maker 0% 手续费**（Taker 要付 1.5-2%）
- **Maker Rebate**：按 volume 返现（这个 Bot 最后一笔 rebate 是 $145）
- **Queue priority**：高频下单排在订单簿前面，成交率更高

## 后续：Bot 已停运

截至 3 月 6 日，这个 Bot 已经停止运行。

最后的操作是大量 REDEEM（130 笔）——批量结算退出。

但 All-time PnL（Leaderboard 数据）显示：累计盈利超过 $113 万。

$67K 部署资金，累计赚了超过 $1.1M。

这就是做市的复利效应——不是某一笔赚大钱，是每分钟 34 单、每单几美分，日复一日。

至于为什么停了——可能是策略调整、可能是换了地址、也可能是 Polymarket 近期调整了延迟规则（500ms delay 被移除后半数 bot 一夜阵亡）。

链上数据只能看到行为，看不到决策。

## 总结

- 做市不是赌方向，是赚价差。100% BUY 是因为两边都买。
- 不是所有品种都赚钱。ETH 和 SOL 赚，BTC 亏。选品是核心能力。
- 做市不是无风险的。单个 BTC 1h candle 可以亏 $2,000，但有自愈能力。
- 频率就是竞争力。Queue priority 决定成交率，高频是基础设施，不是策略。
- 纯做市的上限有天花板，叠加方向信号（如 Binance 实时价格）可以提升 ROI，但也放大了方向错误时的亏损。

**数据基础：** 3,379 笔交易 / 100 分钟采样 + Positions API 持仓快照（2026-02-21）+ 最新 API 数据（2026-03-06）

对链上数据分析感兴趣？更多研究笔记见 leolabs.me/guide | 浏览 Polymarket 市场数据

**免责声明：** 本文为个人研究分析和链上数据观察记录，不构成任何投资建议或交易指导。预测市场存在本金损失风险，请根据自身情况独立判断。文中链接仅供参考，作者可能从中获得推荐奖励。
