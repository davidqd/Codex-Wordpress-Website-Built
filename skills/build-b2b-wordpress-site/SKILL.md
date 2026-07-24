---
name: build-b2b-wordpress-site
description: 为外贸制造商、工业品供应商、批发商和 OEM/ODM 企业规划、搭建、重构并验收专业 WordPress B2B 独立站。用于用户提出外贸建站、B2B 官网、WordPress 企业站、主题 Pattern/Theme Options 学习、参考站视觉重设计、首页或内页改版、产品分类、ACF 产品模板、询盘转化、SEO/GEO 基础结构、响应式检查或通过 WordPress MCP 执行建站时。对所有页面强制采用后台可视化维护模式，并采用 MCP 优先流程：首次采集主题 Pattern 前先验证 MCP 能否读取名称、slug 和原始 Gutenberg 内容，验证失败后才使用浏览器兜底；后续页面优先由 MCP 组合主题 Patterns。
---

# B2B WordPress 建站

以“先设计、再搭建、后发布”为默认工作方式。不得从需求清单直接跳到批量页面制作。

## 必须读取的参考文件

根据当前阶段读取对应文件，不要一次性加载全部内容：

- 制定视觉规范时，读取 [references/design-system.md](references/design-system.md)。
- 规划首页、内页、产品分类或产品详情时，读取 [references/page-blueprints.md](references/page-blueprints.md)。
- 使用 WordPress、主题、MCP、ACF、表单或 SEO 插件执行时，读取 [references/wordpress-execution.md](references/wordpress-execution.md)。
- 采集、缓存或复用主题注册型 Pattern 时，读取 [references/theme-pattern-mcp-workflow.md](references/theme-pattern-mcp-workflow.md)。
- 准备发布或声称完成前，必须读取 [references/quality-gates.md](references/quality-gates.md)。

## 核心原则

1. 把用户需求转换为视觉系统和页面结构，不把模块清单直接堆到页面里。
2. 优先学习并复用当前主题的 Patterns、Theme Options、模板和组件。
3. 参考网站只用于分析布局、节奏和交互，不复制文字、图片、商标或专有代码。
4. 首页是全站设计母版。首页未通过视觉验收前，不批量制作内页。
5. 内容、数据和布局分离：主题/模板负责布局，ACF 负责结构化数据，编辑器负责内容。
6. 不编造工厂面积、产能、认证、客户数量、交期、评价、出口国家或客户 Logo。
7. 前台内容默认使用英文；后台说明和执行报告默认使用中文。
8. 所有写入动作保持小而可验证。保留现有 URL、页面层级和用户内容，除非用户明确要求改变。
9. 参考站重设计必须先锁定页面视觉骨架：全宽或盒装、Header 层数、Hero 类型、首屏占比和图片策略。
10. 不得用大量页面级内联样式代替主题 Pattern、Theme Options、子主题样式或统一样式入口。
11. 结构正确不等于视觉通过。必须在相同视口并排检查参考站和当前站的首屏轮廓、信息密度与视觉重心。
12. 所有页面生成都必须启用“原生可视化组件强制模式”，不得降级为整页 HTML 或页面级 CSS。
13. 页面搭建默认采用“MCP 优先、浏览器兜底”：任何主题 Pattern 浏览器采集之前，必须先验证 WordPress MCP 能否返回注册 Pattern 的名称、slug 和原始 Gutenberg 内容。
14. MCP 能完整读取注册 Pattern 时，首次组件采集也必须使用 MCP；只有 MCP 缺少该能力、权限失败或只能返回名称而没有原始内容时，才允许浏览器采集。
15. 同一主题版本的 Pattern 完成采集和验证后，后续页面不得重复通过浏览器逐个插入。
16. 浏览器用于 MCP 采集失败后的兜底、Theme Options、缺失接口和视觉验收；页面创建、Pattern 组合、内容替换、状态更新和批量内页优先使用 WordPress MCP。

## 原生可视化组件强制模式

本模式适用于首页、内页、产品分类页、产品详情页、博客、联系页、活动落地页和后续新增页面。

1. 正式页面必须由 Gutenberg Blocks、主题 Patterns、主题 Slider 或主题原生组件组成。
2. 每个主要模块必须能在 WordPress 编辑器中独立选中、移动、复制、删除和修改内容。
3. 不允许把完整页面或主要页面区段放进单个 Custom HTML、Classic Block、Shortcode 容器或不可拆分的代码块。
4. 自定义 HTML 只能用于主题与 Gutenberg 确实无法实现的小型局部元素；使用前记录原生方案为何不可行。
5. 页面内容中不得放置 `<style>`，也不得把页面级内联 CSS 作为正式交付方案。
6. 公共样式只能写入子主题或主题 Additional CSS 等统一样式入口；不得直接修改父主题。
7. 开工前必须输出“主题组件能力对照表”，至少包含页面模块、组件来源、Pattern/Block 名称、可编辑字段、采用情况和弃用原因。
8. 产品分类、应用、质量流程、FAQ、RFQ 必须保存为可复用 Pattern；记录 Pattern 名称、ID、同步状态和使用页面。
9. 只需复用结构、不应全站联动内容时，使用非同步 Pattern；需要集中更新的公共模块才使用同步 Pattern。
10. 验收时必须同时检查前台视觉与后台编辑体验，证明主要模块可独立编辑且未退化为整页 HTML。
11. 无法检查 Theme Options、Pattern 编辑器或后台区块结构时，停止 WordPress 页面生成；只能输出组件规划、文本线框或站外视觉稿，不得创建代码堆砌的 WordPress 概念页。
12. 最终报告必须逐项列出每个页面模块使用的主题 Pattern、Gutenberg Block、Slider、表单组件或经批准的自定义补充。
13. 未达到可视化维护要求时，不得发布页面、替换正式首页或声称建站完成。
14. 主题组件采集前必须执行 MCP 能力预检，并记录所用工具、返回字段、权限状态和失败原因。
15. MCP 返回 Pattern 名称、slug 和原始 Gutenberg 内容时，直接建立带主题 slug、版本、依赖和校验信息的组件目录，不进行浏览器采集。
16. MCP 预检失败或内容不完整时，才通过浏览器插入 Pattern Lab，再由 MCP 读取其 Gutenberg 原始结构并固化组件目录。
17. 主题版本和组件目录匹配时，后续页面直接由 MCP 插入 Pattern 原始区块副本或引用已保存的同步 Pattern；不得把浏览器逐块点击作为常规搭建方式。
18. 主题升级、Pattern 校验失效、依赖区块缺失或前台渲染异常时，组件缓存立即失效，并重新从 MCP 能力预检开始，不得直接默认浏览器采集。

页面内容允许使用合法的 Gutenberg 注释标记和由区块编辑器生成的 HTML；禁止的是用一个不可拆分的 HTML 容器伪装成可视化页面。

## 参考站重设计防回归规则

用户提供参考 URL 时，以下步骤属于强制门禁：

1. 在修改 WordPress 前，分别截取参考站 1440px 与 390px 的真实页面画面。
2. 输出参考站视觉合同：Header、Hero、页面框架、内容宽度、字体层级、图片裁切、CTA、组件装饰和深浅节奏。
3. 明确选择 Hero 模型，例如“全宽背景图 + 遮罩 + 居中文案”或“左右分栏”；不得在未说明的情况下换成另一种模型。
4. 盘点主题原生 Patterns、Theme Options、Slider、Header/Footer 与浮动联系模块，记录采用或弃用原因。
5. 先在 Draft、Private、预览副本或不公开 Style Guide 中实现，不直接覆盖已发布首页。
6. 统一样式放入主题支持的全局入口或子主题；只有单一、不可复用的微调允许内联。
7. 在同一视口对比参考站与草稿。若页面框架、首屏高度、视觉焦点或内容密度明显不一致，继续修改，不得把“功能齐全”当成通过。
8. 发布前清除主题演示标语、开发邮箱、默认 Logo、占位联系信息、演示 CTA 和无效社媒链接。
9. 缺少适合 Hero 的高分辨率横图时，明确标记素材风险；不得把小尺寸产品近景强行当作沉浸式全屏背景并宣称达到参考体验。
10. 用户要求“参考某站”时，只复用设计原则与主题能力，不复制其文字、图片、商标或专有代码。

## 标准工作流

### 阶段 0：盘点与范围确认

先进行只读检查：

- 确认域名、WordPress 状态、当前主题、主题版本和子主题。
- 列出页面、菜单、层级、文章、产品分类、媒体和表单。
- 检查 Theme Options、Patterns、模板、插件、SEO、缓存和安全状态。
- 识别首页、产品分类页、产品详情页和博客的数据来源。
- 记录现有 URL、标题、发布状态和可能被覆盖的内容。

首次接触某个主题版本时，先通过工具发现和 WordPress MCP 验证是否能直接读取注册 Pattern 的名称、slug 与原始 Gutenberg 内容；成功时用 MCP 完成采集。只有 MCP 能力不存在、权限失败或内容不完整时，才逐个通过后台浏览器检查和采集 Patterns。区块样式、Slider、Header/Footer Layout 和 Theme Options 仍按实际接口选择 MCP 或浏览器。已有匹配当前主题 slug、版本和依赖的已验证组件目录时，先通过 MCP 复核版本和目录完整性，不重复采集。随后输出或复用主题组件能力对照表：

| 页面模块 | 组件来源 | Pattern / Block / Option | 可编辑字段 | 采用情况 | 弃用原因 |
|---|---|---|---|---|---|

MCP 无法读取注册 Pattern 且浏览器也无法实际检查 Pattern 编辑器，或现有组件目录与主题版本不匹配时，触发强制停止条件，不得进入 WordPress 页面生成。匹配版本的组件目录已经过后台可编辑性和前台视觉验收时，可直接进入 MCP 草稿搭建。

输出简短盘点结果、组件能力对照表和本次范围。没有必要时不要提问；只有缺少的信息会改变架构或造成真实风险时才提一个问题。

### 阶段 1：分析参考与业务证据

如用户提供参考 URL：

1. 使用浏览器在 1440px 与 390px 实际查看参考站和现站。
2. 提取页面框架、Header 层数、Hero 模型、首屏高度、区块顺序、内容宽度、留白、色彩、字体层级、图片比例、卡片、CTA 和页脚逻辑。
3. 用简表记录“参考站特征、当前站状态、实现方式、验收标准”。
4. 区分可借鉴的设计原则、可复用的主题模块与不可复制的资产。

同时建立业务证据表：

- 已确认事实
- 待补资料
- 可安全使用的通用表达
- 禁止上线的未验证声明

### 阶段 2：建立设计合同

在修改页面前先输出并锁定：

- 页面采用全宽、盒装还是混合框架
- Header 层数、Logo 区、导航区和顶部信息条
- 主色、强调色、浅色背景和正文颜色
- 内容最大宽度
- H1/H2/H3、正文和按钮字号
- 区块上下间距
- 卡片边框、圆角、阴影和内边距
- Hero 类型、高度、首屏占比、遮罩、文字宽度和图片裁切
- 图片比例和移动端断点
- 深色区与浅色区的交替规则

具体规则见设计系统参考文件。

### 阶段 3：输出线框图与组件清单

先用文本线框图确定页面节奏，例如：

```text
Header
Hero
Proof / Capability Cards
Company Introduction
Dark Advantages Section
Product Categories
Applications
Quality Process
FAQ + Inquiry Form
Knowledge Center
Footer
```

随后列出复用组件：

- Header / Navigation
- Hero
- Section Heading
- Product Card
- Advantage Card
- Image + Text
- Process Steps
- Parameter Table
- FAQ
- Inquiry Form
- CTA
- Footer

发现两个模块承担同一转化任务时，合并或删除，避免重复 CTA。

给每个线框模块指定实现来源：主题 Pattern、Gutenberg Block、Slider、表单组件、ACF 动态模板或经批准的小型自定义补充。没有实现来源的模块不得进入正式制作。

### 阶段 4：先做组件库和首页草稿

先建立一个不公开的 Style Guide 或 Pattern Library 草稿，展示核心组件。主题已有可用 Pattern 时直接复用。

首次使用某个主题版本时：

1. 先发现并调用 WordPress MCP 的注册 Pattern 读取能力，验证是否同时返回名称、slug 和原始 Gutenberg 内容。
2. MCP 验证成功时，直接读取、拆分和记录组件目录，不打开浏览器采集 Pattern。
3. MCP 能力不存在、权限失败或内容不完整时，记录证据，再由浏览器把所需 Pattern 插入 Pattern Lab 草稿并保存。
4. 浏览器兜底后由 MCP 读取草稿的原始 Gutenberg 标记，按顶级 Pattern 拆分并记录组件目录。
5. 把产品分类、应用、质量流程、FAQ 和 RFQ 固化为可复用 Pattern，记录 ID、同步策略、主题版本和依赖。
6. 后续首页和内页由 MCP 组合这些原生结构、替换业务文案和媒体；不再逐页通过浏览器点击插入。

必须把产品分类、应用、质量流程、FAQ 和 RFQ 保存为可复用 Pattern，并记录 Pattern ID。页面由多个可独立编辑的区块/Pattern 组合，不得用一个 Classic Block 或 Custom HTML 包住完整页面。

然后只制作首页：

1. 保存为 Draft 或使用安全的预览方式。
2. 检查视觉节奏、标题层级、图片质量、按钮和表单。
3. 有参考站时，先在 1440px 与 390px 做同视口首屏对比。
4. 再在 1440、1024、768、390 像素宽度验证完整首页。
5. 修正页面框架偏差、Hero 模型偏差、重复 CTA、横向溢出、图片变形、列宽和留白。
6. 检查 Header/Footer 是否仍含主题演示内容或未确认联系方式。
7. 在后台编辑器逐个选中主要模块，验证其可移动、复制、删除和修改。
8. 检查页面内容不存在页面级 `<style>`、整页 Custom HTML 或整页 Classic Block。

首页未通过验收，不继续批量内页。

### 阶段 5：以首页为母版扩展内页

首页通过后再制作：

- About Us
- Products
- Product Categories
- Applications
- Quality Control
- Production / Factory
- Blog / News
- FAQ
- Contact Us

内页复用相同设计 Token 和组件，但保持不同的信息结构。不要把所有页面做成同一套模块的机械复制。

每个内页继续执行原生可视化组件强制模式；首页通过不代表内页可以降级为手工 HTML。

内页批量搭建必须优先使用 MCP：

- 从已验证的主题组件目录读取 Pattern 原始结构或可复用 Pattern ID。
- 用 MCP 创建 Draft、组合顶级模块、替换文案、图片、链接和表单 ID。
- 保留主题 Pattern metadata、className、核心区块结构和依赖区块。
- 完成一批 MCP 写入后，再集中使用浏览器进行视觉与后台编辑体验抽检，不逐页重复相同的插入点击。

### 阶段 6：产品详情与 ACF

产品较多时使用 ACF 结构化录入：

- 型号、卖点、主图、图库
- 尺寸、压力、温度、材料、连接、驱动和标准
- 特点、应用、包装、定制、PDF、FAQ

先创建一个 Draft 参考产品，确认字段和前台布局，再建立可复用的子主题 PHP 模板。不要为每个产品手工复制整页 HTML。

默认不要启用全局 ACF shortcode。经典主题优先使用子主题 PHP 模板和 `get_field()`；区块主题可在确认版本与安全设置后使用 Block Bindings。

### 阶段 7：SEO、GEO 与转化

为每个核心页面检查：

- 单一 H1 和清晰 H2/H3 层级
- 稳定、可读的 URL
- SEO Title、Meta Description、canonical
- 图片文件名和 ALT
- 产品、分类、应用、质量、生产和联系页之间的内链
- Organization、WebSite、Breadcrumb、Product、FAQ 等 Schema 的适用边界
- 首屏 CTA、页尾 CTA、表单和移动端点击区域

只在真实页面显示相应内容时输出 Schema。

### 阶段 8：验收与发布

按照质量门禁逐项验证。未验证的项目必须写成“未验证”，不得写成已完成。

满足全部发布门禁后才发布：

- 首页通过四个断点检查
- 核心内链有效
- 表单前端显示正常
- 无重复 H1、重复 CTA 或空链接
- 没有虚假证明
- 页面状态和 URL 符合规划
- SEO 抓取设置没有阻止正式站点
- 后台主要模块可独立编辑
- 产品分类、应用、质量流程、FAQ、RFQ 的 Pattern ID 已记录
- 页面内容不存在页面级 `<style>` 或整页 Custom HTML / Classic Block

## 工具选择

- WordPress 内容、页面、菜单、媒体、ACF 值和 SEO 字段：优先使用 WordPress MCP。
- 已采集的主题 Pattern、Gutenberg 结构、同步 Pattern 和批量页面组合：必须优先使用 WordPress MCP。
- 同一主题版本首次 Pattern 采集：必须先通过工具发现验证 MCP 是否能读取注册 Pattern 的名称、slug 和原始 Gutenberg 内容。
- MCP 采集验证成功时禁止使用浏览器采集；验证失败并记录原因后，才允许浏览器建立 Pattern Lab。采集完成后立即由 MCP 固化，后续页面禁止重复走浏览器插入流程。
- 主题或 ACF 后台没有对应 MCP 能力：使用已登录浏览器或 Computer Use。
- 页面布局和响应式检查：必须使用浏览器实际查看，不以 HTML 结构检查替代全部视觉验收。
- 参考站重设计：必须保存同视口视觉证据，不能只读取 DOM 或文字。
- 本地技能文件：使用 `apply_patch` 精准修改。

## 强制停止条件

遇到以下情况时停止发布，但继续完成安全的草稿和只读检查：

- 后台登录失效
- 缺少会改变架构的主题或插件能力
- 尚未盘点主题 Pattern、Theme Options、Header/Footer 或 Slider 能力
- 无法实际查看 Theme Options、Pattern 编辑器或页面区块结构
- 主要模块只能通过不可拆分的整页 HTML 实现
- 必需的可复用 Pattern 尚未建立或无法记录 Pattern ID
- 将覆盖用户现有内容但无法备份或保留修订
- 表单、支付、隐私或联系人信息来源不明确
- 真实证书、工厂数据或客户证明未提供
- 参考站核心体验依赖全屏图片，但现有素材尺寸或构图明显不适合
- 浏览器无法完成关键视觉验证

## 最终交付格式

非简单任务使用：

**假设（Assumption）：** 使用了哪些真实信息、占位符和范围假设。
**修改内容（Changed）：** 页面、组件、主题选项、数据、菜单、表单和 SEO 的实际变化。
**验证情况（Verified）：** 实际检查的 URL、断点、表单、链接、状态和后台可视化编辑能力。
**剩余风险（Remaining risk）：** 未验证项目、待补资料、性能或发布风险。

最终报告附“页面模块实现清单”，逐项列出模块名称、Pattern/Block/Option、Pattern ID、同步状态和自定义补充原因。

先报告结果，再报告过程。不要把计划当成完成结果。
