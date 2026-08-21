# skk-domainset-reject

自动生成的 Mihomo MRS 域名屏蔽规则集，内容来自 [Sukka's Ruleset](https://ruleset.skk.moe)。

## 规则集

| 文件                                                                                   | 来源                                | 说明           |
| -------------------------------------------------------------------------------------- | ----------------------------------- | -------------- |
| [`List/skk_domainset_reject_base.mrs`](List/skk_domainset_reject_base.mrs)             | `reject.conf`                       | 基础拦截列表   |
| [`List/skk_domainset_reject_with_extra.mrs`](List/skk_domainset_reject_with_extra.mrs) | `reject.conf` + `reject_extra.conf` | 基础和扩展列表 |

## 使用方式

在 Mihomo `config.yaml` 的 `rule-providers` 中引用：

```yaml
rule-providers:
  skk_reject_base:
    type: http
    behavior: domain
    format: mrs
    url: "https://raw.githubusercontent.com/Aaakul/domainset-reject-mrs/main/List/skk_domainset_reject_base.mrs"
    interval: 86400
    path: ./rules/skk_domainset_reject_base.mrs
```

```yaml
skk_reject_with_extra:
  type: http
  behavior: domain
  format: mrs
  url: "https://raw.githubusercontent.com/Aaakul/domainset-reject-mrs/main/List/skk_domainset_reject_with_extra.mrs"
  interval: 86400
  path: ./rules/skk_domainset_reject_with_extra.mrs
```

## 自动更新

规则集由 GitHub Actions 每天 UTC 02:00 自动从 Sukka's Ruleset 拉取最新数据并重新生成。  
MRS 文件使用固定版本 **Mihomo v1.19.30** 生成。  
仅在内容发生实际变化时才会产生新的 commit。

## 许可证

本仓库的规则集数据来源于 [SKK Ruleset](https://ruleset.skk.moe)，遵循其原始许可证
[GNU Affero General Public License v3.0（AGPL-3.0）](LICENSE)。
