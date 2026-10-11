# Surge 常用直连规则

覆盖通讯办公、购物支付、内容社区、搜索地图、音乐视频、出行生活、开发，以及 ToDesk、iCloud 与 Mac 常用 Apple 服务。

在 Surge 的 `[Rule]` 段中引用，放在可能抢先匹配的宽泛规则和 `FINAL` 之前：

```ini
RULE-SET,https://raw.githubusercontent.com/byzhangkui/surge-rules/main/direct.list,DIRECT,update-interval=86400
```

本清单为精简起始版，尚未验证全部服务的实际请求链路。`qq.com`、`gtimg.com`、`gtimg.cn` 和 `alicdn.com` 覆盖相应生态的资源。阿里云与腾讯云主要覆盖门户和控制台，未整体放行共享云存储域名。ToDesk 包含 `todesk.com` 及其子域名，其他连接域名需从请求列表确认后补充。

参考：
- https://raw.githubusercontent.com/Loyalsoldier/surge-rules/release/ruleset/direct.txt
- https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Surge
- https://manual.nssurge.com/rules/ruleset.html

## Apple / Mac 服务

按用户选择将 iCloud、Apple 账号、App Store、系统更新与恢复、推送、证书和应用验证、Siri、Spotlight、地图及常用内容下载设为直连。按服务域名维护，不整体放行 `apple.com`。`icloud.com` 同时覆盖 Private Relay 的 `mask`、`mask-h2`、`mask-api` 子域名。Apple Intelligence 的第三方 Private Cloud Compute 中继未纳入本次范围。

这些是全球 Apple 服务，直连是本清单的路由选择，不表示其服务器一定在国内，也不保证直连更快；尚未在实际 Mac 上验证全部请求链路。

手工验证：更新 Surge 远程规则集后，分别检查 iCloud 文件/照片同步、Apple 账号登录、App Store 下载及软件更新的请求，确认命中本规则集并使用 DIRECT。

官方域名来源：https://support.apple.com/en-us/101555

## 国内大模型 API

覆盖 DeepSeek、GLM/智谱、通义千问/百炼、豆包/火山方舟、腾讯混元、百度千帆、Kimi、MiniMax、讯飞星火的已核对常用 API 入口。固定主机使用 DOMAIN 精确匹配；百炼北京地域工作空间入口使用限定的 DOMAIN-SUFFIX。混元 OpenAI 兼容入口已被现有 cloud.tencent.com 后缀覆盖。各规则注释附官方来源。

本次没有纳入海外区域入口、第三方转发平台或整个共享云域名。仅验证规则内容与发布结果，未发起带密钥的模型调用；实际调用与 DIRECT 命中需在 Surge 请求列表验证。
