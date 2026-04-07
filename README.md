# clashrule

个人维护的 OpenClash / ACL4SSR 订阅转换规则仓库。

这个仓库的定位不是做通用大而全模板，而是基于 ACL4SSR 的现成规则体系，叠加我自己的自定义分流、补充规则和 IPTV 内容，方便在 OpenClash 里直接引用使用。

## 仓库结构

### 核心配置
- `jjyy.ini`：当前主用的订阅转换模板，优先维护这个文件
- `ACL4SSR Online change.ini`：较早期的改版模板，保留作参考
- `ACL4SSR_Online_Full.ini`：ACL4SSR 风格的完整模板备份/参考

### 自定义规则集
- `AI.list`：AI / Copilot / Claude / Gemini / Bing 等相关规则
- `Direct.list`：需要强制直连的补充规则
- `Disney.list`：Disney+ 相关规则
- `ProxyLite.list`：补充走代理的轻量规则
- `ProxyLiteMTP.list`：额外代理规则补充
- `emby.list`：Emby 相关分流
- `new.list`：新增但尚未归类的临时规则池

### 其它文件
- `iptv.m3u`：自用 IPTV 列表
- `result.m3u`：较大的结果文件/聚合输出

## 使用方式

### 1. 在 OpenClash / ACL4SSR 订阅转换中引用
主配置文件：

```text
https://raw.githubusercontent.com/jjyy7783/clashrule/main/jjyy.ini
```

### 2. 自定义规则集引用
`jjyy.ini` 已经直接引用本仓库里的这些文件：
- `new.list`
- `emby.list`
- `Direct.list`
- `ProxyLite.list`
- `ProxyLiteMTP.list`
- `AI.list`
- `Disney.list`

也就是说，后续只要更新这些 `.list` 文件并推送到本仓库，OpenClash 重新拉取配置后就会生效。

## 维护原则

### 新增规则怎么处理
- 暂时拿不准归类时，先放进 `new.list`
- 确认用途后，再移动到对应规则文件
- `new.list` 只保留临时池属性，避免长期堆积成第二个杂项仓库
- 尽量避免同一条规则在多个文件里重复出现

### 修改时优先注意
- 优先维护 `jjyy.ini` 和各个 `.list` 文件，不要直接堆一堆历史备份
- 尽量修明显错误、重复项、失效域名，避免大改导致原本可用规则翻车
- 自定义规则源统一使用当前仓库：`jjyy7783/clashrule`

### 不建议随便动的部分
- 各策略组名称
- 已被 OpenClash / 订阅转换面板引用的主配置路径
- 已经长期稳定可用的地区分组结构

## 当前状态
- 当前主维护模板：`jjyy.ini`
- 当前主仓库：`jjyy7783/clashrule`
- 上游参考仓库仍保留为：`yjp8662/clashrule`
- 当前 GitHub Issues / PR / Actions 未启用，日常维护以直接提交为主

## 日常维护建议
- 优先检查 `jjyy.ini` 中引用的自定义规则文件是否仍然存在且路径一致
- 自定义 raw 链接统一使用 `https://raw.githubusercontent.com/jjyy7783/clashrule/main/...` 形式，减少混用 `refs/heads/main`
- 当前与 `upstream/main` 的 `jjyy.ini` 核心差异，主要就是自定义规则源已切换到当前 fork；上游暂未出现必须同步的新改动
- 如需跟进上游变化，先对比 `upstream/main` 与当前仓库差异，再决定是否选择性同步

## 致谢 / 参考
- ACL4SSR：<https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config>
- 七尺宇模板（原 README 提到的参考来源）
- Emby 规则中包含自用服务器，不代表官方服务
