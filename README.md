# 阿尔法猎手 · ALPHA HUNTER

轻量级 A 股智能选股终端 —— 单文件 HTML，打开即用。

**在线地址**：https://toukaitetsuya3150-code.github.io/alpha-hunter/

## 功能

- 多因子横截面打分：动量 / 量能 / 估值 / 风险 / 成长（iFinD 盈利预测）
- 全市场扫描 / 底部突破扫描 / 主线板块扫描
- 模拟交易（虚拟买卖、自动结算）
- 个股分析：日 K 线 + DCF 估值 + 信号诊断
- 历史数据库：打分记录自动跟踪结算
- 远程版本检查：打开自动提示更新

## 数据

- 实时行情：东方财富 push2（JSONP，免跨域）
- 日 K：腾讯行情接口
- 所有用户数据仅存浏览器 localStorage，无服务器状态

## 部署

见 [DEPLOY.md](DEPLOY.md)。静态托管，无构建，GitHub Pages 直接服务根目录即可。

⚠️ 仅供研究，不构成投资建议。
