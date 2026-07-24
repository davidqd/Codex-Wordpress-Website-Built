# WordPress 执行规范

## 目录

1. 工具路由
2. 修改顺序
3. 主题与 Pattern
4. ACF
5. 表单
6. SEO/GEO
7. 缓存与回滚

## 1. 工具路由

- 页面、文章、菜单、媒体、插件、主题、SEO 和 ACF 字段值：优先 WordPress MCP。
- 已采集的主题 Pattern、Gutenberg 原始结构、可复用 Pattern 和页面批量组装：必须优先 WordPress MCP。
- Theme Options、ACF 字段组导入和没有 MCP 能力的后台功能：使用已登录浏览器。
- 视觉和响应式：使用浏览器截图或真实视口检查。
- 不用浏览器 UI 代替已有的语义化 MCP 操作。
- 主题 Pattern 首次采集前先通过工具发现和实际只读调用验证 MCP；未验证 MCP 失败，不得直接使用浏览器采集。
- 同一主题版本不得为每个页面重复通过浏览器插入 Pattern；浏览器只负责首次采集、缺失接口和验收。

## 2. 修改顺序

1. 只读盘点。
2. 记录页面 ID、URL、父级、状态和更新时间。
3. 有参考站时，先保存参考站桌面端与移动端视觉证据。
4. 盘点 Theme Options、Patterns、Header/Footer、Slider 和浮动联系模块。
5. 检查是否存在与当前主题 slug、版本和依赖匹配的已验证 Pattern 组件目录。
6. 没有有效目录时，先发现并实际调用 MCP 候选工具，验证能否读取注册 Pattern 的名称、slug 和原始 Gutenberg 内容。
7. MCP 验证成功时直接固化组件目录；失败并记录原因后，才用浏览器建立一次 Pattern Lab，再由 MCP 读取原始结构。
8. 由 MCP 先修改一个草稿页面或预览副本。
9. 验证组件、视觉相似度与响应式。
10. 用户确认或质量门禁通过后再更新正式首页。
11. 首页验收后由 MCP 批量搭建内页。
12. 最后更新菜单、SEO 和缓存。

更新现有页面，不创建重复的 Home、Products 或 Contact 页面。

## 3. 主题与 Pattern

- 读取当前主题名称、版本和父/子主题状态。
- 首次接触某个主题版本时，在后台逐个查看可用 Patterns、区块样式、Slider、Header/Footer Layout 和 Theme Options；只读取名称列表不算完成盘点。
- 已有匹配当前主题版本的已验证组件目录时，使用 MCP 复核版本、依赖、Pattern slug 和校验状态，不重复进行逐页浏览器插入。
- 开工前输出主题组件能力对照表：页面模块、组件来源、Pattern/Block/Option 名称、可编辑字段、采用情况和弃用原因。
- 对参考站中的 Header、Hero、Slider、浮动联系栏、语言切换和 Footer，逐项确认主题是否已有对应模块。
- 优先通过 Theme Options 调整 Header 层数、Logo、顶部信息条、按钮和联系方式。
- 能用主题模块实现时不引入重型页面构建器。
- 公共 CSS 放入子主题或统一样式入口，不在几十个页面重复内联。
- 正式页面只使用 Gutenberg Blocks、主题 Patterns、主题 Slider 或主题原生组件组合。
- 每个主要模块必须能在后台独立选中、移动、复制、删除和修改。
- 不把完整页面或主要区段放进单个 Custom HTML、Classic Block、Shortcode 容器或不可拆分代码块。
- 页面内容中不得放置 `<style>`；不得使用页面级内联 CSS 完成正式交付。
- 如果不得不用自定义 HTML，仅用于原生组件无法实现的小型局部元素，记录原因，把样式集中到子主题或 Additional CSS，并先在草稿中验证。
- 不直接修改会被更新覆盖的父主题。

### 3.1 MCP 优先的 Pattern 固化

先验证 MCP：

1. 通过工具发现查找 registered patterns、block patterns、theme data、通用 REST 或等价只读能力。
2. 实际调用候选工具，确认返回 Pattern 名称、稳定 slug/`patternName` 和包含 Gutenberg 注释的原始 content。
3. 验证成功时直接建立组件目录，不使用浏览器采集。
4. 只返回名称、分类或预览，不算成功。

MCP 能力不存在、权限失败、接口错误或内容不完整时：

1. 记录候选工具、状态和失败原因。
2. 浏览器建立 `Theme Pattern Lab — {theme-slug} {version}` 草稿。
3. 把当前项目需要的主题 Pattern 各插入一次并保存。
4. MCP 读取 raw Gutenberg content，按 `metadata.patternName`、Pattern slug 或已确认的顶级 Group 拆分。
5. 记录主题版本、Pattern slug、可编辑字段、自定义区块依赖、媒体依赖和结构校验值。

两条采集路径都必须：

1. 将产品分类、应用、质量流程、FAQ、RFQ 创建为可复用 Pattern 并记录 ID。
2. 后续页面由 MCP 复制原始 Gutenberg 结构或引用同步 Pattern；禁止再逐页浏览器点击插入。

MCP 写入时保留主题 metadata、className、区块层级和自定义区块名称，只替换业务文案、媒体、ALT、链接、按钮和真实表单 ID。不得把前台渲染后的普通 HTML 当成 Pattern 原始结构写回。

主题 slug/版本变化、Pattern 校验失败、依赖区块缺失、区块编辑器报错或前台样式失效时，缓存失效；只重新采集受影响 Pattern。

必须建立并记录以下可复用 Pattern：

| Pattern | 默认同步策略 | 必须记录 |
|---|---|---|
| 产品分类 | 非同步，除非全站需要集中更新 | 名称、ID、使用页面 |
| 应用 | 非同步，除非全站需要集中更新 | 名称、ID、使用页面 |
| 质量流程 | 非同步或同步，按内容所有权决定 | 名称、ID、使用页面 |
| FAQ | 非同步；统一问答才同步 | 名称、ID、使用页面 |
| RFQ | 同步结构；表单本身使用真实表单组件 | 名称、ID、表单 ID、使用页面 |

MCP 无法读取注册 Pattern、浏览器也无法查看 Pattern 编辑器或页面区块树，且没有匹配版本的已验证组件目录时，不得生成 WordPress 页面；只输出文本线框、组件规划或站外视觉稿。

发布前检查并移除：

- 主题演示标语和开发邮箱
- 默认 Logo、域名占位 Logo 或演示品牌名
- 演示电话、地址、社媒链接和 CTA
- 与用户业务无关的语言切换或浮动按钮

## 4. ACF

产品数量较多时：

1. 创建字段组并开启 REST API。
2. 把字段组绑定到产品 CPT、特定模板或产品分类的子页面。
3. 使用文本、图片、文件、选择等简单字段。
4. ACF Free 没有 Gallery/Repeater 时，用有限图片字段或重新评估数据模型。
5. 创建一个 Draft 产品并填入示例数据。
6. 通过 MCP 读取字段值，确认写入成功。
7. 通过子主题 PHP 模板动态输出字段。

不要把静态参考页误称为动态 ACF 模板。只有修改 ACF 后前台自动变化，才算完成动态绑定。

## 5. 表单

- 先列出现有表单和 ID。
- 优先复用已创建表单。
- 检查 shortcode 是否只出现一次。
- RFQ Pattern 必须使用真实表单区块或 Shortcode Block，不把表单和整页内容一起封装进 Custom HTML。
- 前端检查字段、按钮、成功提示和移动端。
- 未经用户授权，不提交真实询盘测试。

## 6. SEO/GEO

- 先检查现有 SEO 插件，避免安装重复插件。
- 更新 Title、Description、canonical 和 robots 时记录页面 ID。
- 草稿或参考页保持 Draft/Private，避免示例数据被索引。
- Product Schema 只放在真实产品详情页。
- FAQ Schema 只使用页面真实显示的问答。
- Organization 数据必须来自真实公司资料。

## 7. 缓存与回滚

- 利用 WordPress 修订保留可恢复版本。
- 参考站重设计默认不直接覆盖已发布首页；先使用 Draft、Private、预览副本或修订保护。
- 不覆盖无关页面。
- 修改后检查 LiteSpeed/CDN 缓存影响。
- 页面仍显示旧内容时，先确认数据库内容，再清缓存。
- 缓存清理不能替代真实验证。

## 8. 后台可视化验收

对每个新建或重构页面执行：

1. 打开后台编辑器的区块列表视图。
2. 确认 Hero、产品、应用、质量、FAQ、RFQ 和 CTA 等主要模块是独立区块或 Pattern。
3. 逐项验证模块可选中、移动、复制、删除和编辑；验收时不实际保存破坏性测试改动。
4. 确认没有单个 Custom HTML 或 Classic Block 承载完整页面或主要页面区段。
5. 确认页面内容没有 `<style>`，公共 CSS 位于子主题或 Additional CSS。
6. 记录采用的 Pattern/Block/Theme Option、Pattern ID、同步状态和自定义补充原因。
7. 再进行 1440、1024、768、390 前台视觉验收。

后台或前台任一项未通过，页面保持 Draft/Private，不替换正式页面。
