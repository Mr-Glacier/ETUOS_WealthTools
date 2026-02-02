# ETUOS_WealthTools

ETUOS_WealthTools 是一个基于 Python 的轻量级财富管理与盯盘工具集合，旨在为个人投资者、量化学习者与技术爱好者提供行情监控、策略提醒与数据分析能力。

---

## 项目简介

ETUOS_WealthTools 致力于构建一个：

- 易扩展
- 低成本
- 模块化
- 适合个人使用

的盯盘与策略提醒工具。

适用场景：

- 自选股盯盘
- 价格提醒
- 技术指标监控
- 板块异动提醒
- 日内波动监控
- 邮件 / 微信 / 钉钉 / 飞书通知

---

## 核心特性

### 多数据源支持
支持 AkShare、TuShare 以及自定义数据源扩展。

### 策略自定义
支持用户定义价格、涨跌幅、均线等多种监控策略。

### 模块化架构
数据层、策略层、通知层解耦，易于维护与扩展。

### 稳定性设计
内置缓存、限流、重试机制，提升系统健壮性。

---

## 技术栈

- Python 3.8+
- AkShare
- Pandas
- Requests
- Redis / SQLite（可选）
- Flask / FastAPI（可选）
- PyQt（可选）

---

## 项目结构（示例）

```
ETUOS_WealthTools/
│
├── etuos/
│   ├── data/        # 行情数据获取
│   ├── cache/       # 缓存模块
│   ├── monitor/     # 策略监控
│   ├── notify/      # 通知推送
│   └── utils/       # 工具函数
│
├── config.yaml      # 配置文件
├── main.py          # 启动入口
└── requirements.txt # 依赖列表
```

---

## 安装方式

### 克隆仓库

```
git clone https://github.com/your-org/ETUOS_WealthTools.git
cd ETUOS_WealthTools
```

### 创建虚拟环境

```
python -m venv venv
```

Windows:
```
venv\Scripts\activate
```

Linux / Mac:
```
source venv/bin/activate
```

### 安装依赖

```
pip install -r requirements.txt
```

---

## 配置示例（config.yaml）

```
data_source:
  akshare: true

watchlist:
  - symbol: "000001"
    name: "平安银行"
    target_price: 16.00

notify:
  email:
    enable: true
    smtp: smtp.xxx.com
    username: test@xx.com
    password: xxx
```

---

## 快速开始示例

### 获取行情

```
from etuos.data import MarketData

md = MarketData()
quote = md.get_price("000001")
print(quote)
```

### 简单策略监控

```
from etuos.monitor import Monitor

monitor = Monitor()

monitor.watch(
    symbol="000001",
    condition=lambda p: p > 16,
    callback=lambda p: print("价格突破:", p)
)

monitor.run(interval=10)
```

---

## 数据源说明

| 数据源 | 实时性 | 备注 |
|--------|--------|------|
| AkShare | 近实时 | 免费，适合个人使用 |
| TuShare | 延迟/实时 | 部分接口需要 Token |
| 自定义 | 取决实现 | 可扩展 |

---

## 注意事项

- AkShare 属于网页数据抓取封装，可能因网站改版失效。
- 高频请求可能被限流，建议使用缓存。
- 本工具仅用于辅助分析，不构成投资建议。

---

## 未来规划

- Web 可视化界面
- 桌面客户端
- 历史数据回测
- AI 策略分析
- 多账户管理

---

## License

MIT License
