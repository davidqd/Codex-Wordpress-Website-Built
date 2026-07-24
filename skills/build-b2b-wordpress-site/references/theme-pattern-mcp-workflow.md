# 主题 Pattern 的 MCP 优先工作流

## 目录

1. 目标
2. 路由判定
3. 首次采集
4. 组件目录
5. MCP 页面组装
6. 同步策略
7. 缓存失效与回退
8. 验收证据

## 1. 目标

把浏览器从“每个页面的搭建工具”降为“首次采集、专有设置和视觉验收工具”。同一主题版本完成一次 Pattern 采集后，后续页面使用 WordPress MCP 组合原生 Gutenberg 结构。

不得为了追求 MCP 覆盖率而手写近似 Pattern。MCP 使用的必须是从当前主题实际采集并验证过的原始区块结构。

## 2. 路由判定

按以下顺序选择执行方式：

1. 先通过工具发现检查 WordPress MCP 是否提供注册 Pattern、通用 REST、主题数据或等价读取能力。
2. 实际调用候选 MCP 工具，验证能否同时返回 Pattern 名称、slug 和原始 Gutenberg 内容。
3. MCP 验证成功：全程使用 MCP 采集，不打开浏览器采集 Pattern。
4. 已有与当前主题 slug、版本和依赖匹配的已验证组件目录：使用 MCP。
5. MCP 能力不存在、权限失败或只能返回名称而没有原始内容，且没有有效组件目录：记录失败证据后，浏览器只执行一次 Pattern Lab 采集。
6. Theme Options、Header/Footer Layout、主题 Slider 配置没有 MCP 接口：浏览器修改，随后记录结果。
7. 前台视觉、交互和断点检查：使用浏览器。

MCP 采集成功或有效组件目录存在时，不得回退到浏览器采集。只返回 Pattern 名称、分类或预览而没有 Gutenberg 原始内容，不算 MCP 采集成功。

## 3. 首次采集

### 3.1 MCP 直接采集

首次主题版本先执行：

1. 记录活动主题 slug、版本、父/子主题和依赖插件。
2. 发现 WordPress MCP 中与 registered patterns、block patterns、theme data、REST request 相关的工具。
3. 调用最匹配的只读工具，不用浏览器先行探测。
4. 检查返回结果是否包含 Pattern 名称、稳定 slug/`patternName` 和带 Gutenberg 注释的原始 content。
5. 成功时计算结构校验值、建立组件目录，并将业务复用模块创建为可复用 Pattern。
6. 记录 MCP 工具名称、返回字段和成功结果。

### 3.2 浏览器兜底采集

只有 3.1 失败时，才为该主题版本建立 Draft/Private 的 `Theme Pattern Lab — {theme-slug} {version}`：

1. 记录 MCP 失败类型：无工具、无权限、接口错误、只返回名称或缺少原始 content。
2. 在浏览器中逐个查看主题 Pattern 的真实预览、区块树和可编辑字段。
3. 只把当前站点可能使用的 Pattern 插入 Pattern Lab；无需把无关模块写入页面。
4. 保存草稿，不发布。
5. 使用 MCP 读取 Pattern Lab 的 raw Gutenberg content。
6. 按顶级 Pattern metadata、`patternName`、区块边界或已确认的顶级 Group 拆分。
7. 检查每段包含合法 Gutenberg 注释，不含整段 Classic Block、Custom HTML 或页面级 `<style>`。
8. 将业务复用模块创建为可复用 Pattern，并记录 ID；其余模块保存为可复制的原始结构目录。

浏览器采集完成后，普通页面不得再次通过浏览器逐个插入同一批 Pattern。

## 4. 组件目录

组件目录至少记录：

| 字段 | 说明 |
|---|---|
| theme_slug | 活动主题目录名 |
| theme_version | 采集时主题版本 |
| parent_theme | 父主题 slug 或空 |
| pattern_name | 后台显示名称 |
| pattern_slug | `patternName` 或稳定标识 |
| category | 主题 Pattern 分类 |
| source | 主题注册 Pattern、核心 Block、插件 Block 或同步 Pattern |
| reusable_block_id | 已创建时记录 ID |
| sync_strategy | copy、synced 或 unsynced |
| dependencies | 自定义区块、插件、主题脚本和媒体依赖 |
| editable_fields | 标题、正文、图片、按钮、链接、表单等 |
| checksum | 原始 Gutenberg 结构的校验值 |
| verified_at | 最近一次后台和前台验收时间 |
| used_pages | 使用页面 ID |

组件目录可保存在站点工作区、Pattern Library 文档或 WordPress 可复用 Pattern 中。不得把凭据、nonce 或后台 Cookie 写入缓存。

## 5. MCP 页面组装

使用 MCP 搭建页面时：

1. 读取目标页面和组件目录，保留现有 URL、状态和用户内容。
2. 选择与线框模块对应的已验证 Pattern。
3. 使用原始 Gutenberg 标记的独立副本，或使用 `core/block` 引用同步 Pattern。
4. 只替换业务字段：标题、正文、图片、ALT、按钮、链接、表单 ID 和经过确认的数据。
5. 保留 `metadata.patternName`、主题 className、区块层级和自定义区块名称。
6. 先写入 Draft/Private。
7. MCP 重新读取页面并检查 Pattern 数量、H1、表单 ID、Classic/HTML/style、演示内容和页面状态。
8. 批量内页完成后集中进行浏览器验收。

不得把 Pattern 渲染后的普通 HTML 当成 Pattern 原始结构写回页面；必须使用 Gutenberg 注释标记。

## 6. 同步策略

- `copy`：从已验证 Pattern 原始结构复制到页面。适用于文案和图片按页面独立维护。
- `synced`：页面使用 `<!-- wp:block {"ref":ID} /-->` 引用。适用于全站统一维护的 RFQ、公共 CTA 或统一 FAQ。
- `unsynced`：MCP 支持 Pattern 同步状态时保存为 unsynced；不支持时使用 `copy`，同时保留来源 Pattern ID 或目录记录。

产品分类、应用、质量流程和页面专属 FAQ 默认使用 `copy/unsynced`。公共 RFQ 结构默认使用 `synced`，表单使用真实 WPForms/表单区块或独立 Shortcode Block。

## 7. 缓存失效与回退

以下任一条件出现时停止使用缓存并重新采集：

- 活动主题 slug 或版本变化。
- 父主题、子主题或依赖插件变化影响区块。
- Pattern slug 消失、结构校验值变化或必要 className 缺失。
- 页面出现“此区块包含意外或无效内容”。
- 自定义区块未注册，前台 Slider、Query、表单或交互失效。
- 浏览器视觉检查显示主题样式没有应用。

失效后只重新采集受影响 Pattern，不重新搭建已验证的无关模块。

## 8. 验收证据

最终报告增加：

- Pattern 获取路径：MCP 直读、有效缓存或首次浏览器采集。
- MCP 采集预检使用的工具、返回字段、成功结果或失败原因。
- 主题 slug、版本和目录校验状态。
- 页面是否通过 MCP 创建与组合。
- 浏览器是否仅用于 Theme Options、缺失接口和验收。
- 每个模块的 Pattern slug、可复用 Pattern ID、同步策略和使用页面。
- MCP 回读得到的顶级 Pattern 数量、H1、表单 ID、Classic/HTML/style 检查结果。
- 浏览器检查的后台区块树和 1440、1024、768、390 前台结果。
