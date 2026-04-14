# Repository Guidelines

## 项目结构和模块组织
这个仓库保存的是 OpenClash 与 Clash Meta 的配置资源，不是应用程序代码。`Clash-Sands.ini` 是主规则生成器配置；`list/` 存放按服务拆分的规则列表，如 `GitHub.list`、`Netflix.list`、`RU.list`；`yaml/` 存放完整 Clash 配置，如 `clash-fallback.yaml`；`ini/openclash.txt` 是 OpenWrt OpenClash 的 UCI 风格导出配置；`others/` 存放仪表盘相关预设，如 `zashboard-settings.json`。

## 开发、校验与发布
这个仓库没有编译步骤，核心工作是修改和校验配置。改动完成后，优先检查 `yaml/` 下文件格式是否正确，并确认新增规则、策略组、规则集引用没有拼写错误。发布前先查看 `git diff`，确认只包含本次需要的配置变更；如需发版或同步远程仓库，可直接提交并推送。

## 代码风格和命名约定
保留各类文件原有格式。YAML 使用两个空格缩进；`.ini` 和 UCI 风格配置保持每行一条指令；`.list` 文件保持每行一条规则，并使用大写的 Clash 规则类型，例如 `DOMAIN-SUFFIX,github.com`。文件名应清晰且稳定：服务规则列表使用 `TopicCase.list`，YAML 配置文件使用 kebab-case。已被规则或代理组引用的中文标签、表情和分组名称不要随意改动；新增内容也应延续现有风格。

## 提交和 Pull Request 约定
提交信息保持简短、直接，通常使用祈使句并尽量带上文件名，例如 `Update RU.list`、`Create RU.list`。一次提交只处理一个逻辑上的配置变更，避免把无关调整混在一起。Pull Request 需要说明本次改动影响了哪些路由或策略组，列出受影响文件；只有仪表盘设置或可见界面行为发生变化时，才需要附截图。

## 安全和敏感信息
提交前检查 `yaml/*.yaml`、`ini/openclash.txt` 和 `others/zashboard-settings.json`，避免把订阅地址、Token、密码、控制器密钥、邮箱凭据或个人专用地址直接提交到仓库。发现敏感信息时，先脱敏再提交。

## 协作约定
默认始终使用中文回复，且尽量简短。只要需求明确，直接修改文件并给出结果，不要停留在泛泛建议上。除非我明确要求，否则不要回退我已经做过的改动。
