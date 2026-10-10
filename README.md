# Surge 国内常用直连规则

覆盖通讯办公、购物支付、内容社区、搜索地图、音乐视频、出行生活、开发，以及 ToDesk。

在 Surge 的 `[Rule]` 段中引用，放在可能抢先匹配的宽泛规则和 `FINAL` 之前：

```ini
RULE-SET,https://raw.githubusercontent.com/byzhangkui/surge-rules/main/direct.list,DIRECT,update-interval=86400
```

本清单为精简起始版，尚未验证全部服务的实际请求链路。`qq.com`、`gtimg.com`、`gtimg.cn` 和 `alicdn.com` 覆盖相应生态的资源。阿里云与腾讯云主要覆盖门户和控制台，未整体放行共享云存储域名。ToDesk 包含 `todesk.com` 及其子域名，其他连接域名需从请求列表确认后补充。

参考：
- https://raw.githubusercontent.com/Loyalsoldier/surge-rules/release/ruleset/direct.txt
- https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Surge
- https://manual.nssurge.com/rules/ruleset.html
