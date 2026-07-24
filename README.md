# Codex WordPress B2B 独立站建站 Skill

这是一个面向外贸制造商、工业品供应商、批发商及 OEM/ODM 企业的 Codex Skill，用于规划、搭建、重构和验收专业的 WordPress B2B 独立站。

Skill 强制采用“后台可视化维护”模式，优先复用当前 WordPress 主题自带的 Gutenberg Blocks、Patterns、Slider、Header/Footer Layout 和 Theme Options，并通过 WordPress MCP 完成页面创建、内容替换、Pattern 组合和结构校验。

## 主要能力

- 规划外贸 B2B 企业站的信息架构、页面层级和导航结构
- 分析参考网站的版式、视觉节奏、Hero 模型和响应式体验
- 盘点主题 Patterns、区块样式、Slider、Header/Footer 与 Theme Options
- 使用主题原生组件搭建首页、内页、产品分类页和联系页
- 建立产品分类、应用、质量流程、FAQ、RFQ 等可复用 Pattern
- 使用 ACF 规划结构化产品数据和产品详情页模板
- 复用已经创建的 WPForms 询盘表单
- 配置 SEO/GEO 基础结构、页面标题层级、内链和 Schema 建议
- 检查 1440、1024、768、390 四个响应式断点
- 同时验收前台视觉效果和 WordPress 后台编辑体验

## 核心原则

### 1. MCP 优先，浏览器兜底

首次使用某个主题版本时，先验证 WordPress MCP 能否读取注册 Pattern 的名称、slug 和原始 Gutenberg 内容。

- MCP 能完整读取：直接建立组件目录，不使用浏览器采集 Pattern
- MCP 缺少能力、权限失败或内容不完整：使用浏览器建立 Pattern Lab，再由 MCP 读取并固化原始区块结构
- 同一主题版本完成采集后：后续页面必须优先通过 MCP 组合，不再逐页使用浏览器点击插入

浏览器主要用于：

- MCP 无法处理的 Theme Options
- Header/Footer Layout 和主题专有设置
- 后台区块编辑体验检查
- 前台视觉、交互和响应式验收

### 2. 原生可视化组件强制模式

正式页面必须由以下组件组成：

- Gutenberg Blocks
- 主题 Patterns
- 主题 Slider
- 主题原生组件
- 已保存的可复用 Pattern
- 真实的表单区块或 Shortcode Block

每个主要模块必须能在 WordPress 编辑器中独立选中、移动、复制、删除和修改。

禁止：

- 把完整页面放进一个 Custom HTML Block
- 把主要页面区段放进 Classic Block
- 使用页面级 `<style>` 作为正式交付方案
- 用大量内联 CSS 重造主题已经具备的组件
- 在没有视觉验收的情况下直接替换正式首页

### 3. 先设计、再搭建、后发布

默认工作顺序：

1. 盘点 WordPress、主题、插件、页面、菜单、媒体和表单
2. 建立业务证据表，区分真实资料与待确认资料
3. 输出主题组件能力对照表
4. 建立设计 Token 和页面视觉合同
5. 输出页面线框图和组件清单
6. 创建 Style Guide 或 Pattern Library 草稿
7. 使用原生组件完成首页草稿
8. 验收首页视觉和后台编辑体验
9. 以通过验收的首页为母版扩展内页
10. 完成 SEO、GEO、转化和发布检查

## 支持的页面

- Home
- About Us
- Products
- Product Category
- Product Detail
- Applications
- Quality Control
- Production / Factory
- Blog / News
- FAQ
- Contact Us
- B2B 营销落地页

## 推荐目录结构

```text
Codex-Wordpress-Website-Built/
├── README.md
└── skills/
    └── build-b2b-wordpress-site/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── design-system.md
            ├── page-blueprints.md
            ├── quality-gates.md
            ├── theme-pattern-mcp-workflow.md
            └── wordpress-execution.md
```

## 文件说明

| 文件 | 用途 |
|---|---|
| `SKILL.md` | Skill 的核心规则、工作流程、工具选择和停止条件 |
| `agents/openai.yaml` | Codex Skill 列表中的显示名称、简介和默认提示词 |
| `references/design-system.md` | 工业 B2B 网站的设计 Token、视觉节奏和响应式规则 |
| `references/page-blueprints.md` | 首页、内页、产品分类和产品详情页的信息结构 |
| `references/quality-gates.md` | 设计、内容、技术、SEO、转化和发布质量门禁 |
| `references/theme-pattern-mcp-workflow.md` | 主题 Pattern 的 MCP 采集、缓存、复用与失效流程 |
| `references/wordpress-execution.md` | WordPress、ACF、表单、SEO、缓存和后台执行规范 |

## 安装方法

### 方法一：克隆仓库后复制 Skill

```bash
git clone https://github.com/davidqd/Codex-Wordpress-Website-Built.git
mkdir -p ~/.codex/skills
cp -R Codex-Wordpress-Website-Built/skills/build-b2b-wordpress-site ~/.codex/skills/
```

复制完成后，重新打开 Codex 或刷新 Skill 列表。

### 方法二：只下载 Skill 文件夹

下载仓库后，将以下目录完整复制到 Codex 的 Skills 目录：

```text
skills/build-b2b-wordpress-site
```

默认目标位置：

```text
~/.codex/skills/build-b2b-wordpress-site
```

请保留 `references` 和 `agents` 子目录，不能只复制 `SKILL.md`。

## 使用方法

在 Codex 中显式调用：

```text
使用 $build-b2b-wordpress-site，为一家工业阀门制造商规划并搭建专业的外贸 B2B WordPress 网站。
```

参考站重设计示例：

```text
使用 $build-b2b-wordpress-site，参考 https://example.com/ 的视觉节奏，
用当前 WordPress 主题的原生 Patterns 重新设计首页。
先创建草稿，不要直接覆盖正式首页。
```

液压油缸落地页示例：

```text
使用 $build-b2b-wordpress-site，为液压油缸制造商制作一个英文首页落地页。
目标客户是海外 OEM、设备制造商和批发商。
页面必须使用 Gutenberg Blocks、主题 Patterns 和现有 WPForms 表单。
```

内页扩展示例：

```text
使用 $build-b2b-wordpress-site，检查已经通过验收的首页，
以首页设计系统为母版制作 About Us、Applications、Quality Control 和 Contact Us。
```

## 主题组件能力对照表

正式搭建前，Skill 会要求输出类似以下表格：

| 页面模块 | 组件来源 | Pattern / Block / Option | 可编辑字段 | 采用情况 | 弃用原因 |
|---|---|---|---|---|---|
| Hero | 主题 Pattern | Hero Slider | 图片、标题、说明、按钮、链接 | 采用 | — |
| 产品分类 | 主题 Pattern | Product Grid | 标题、图片、说明、链接 | 采用 | — |
| FAQ | Gutenberg | Details Blocks | 问题、答案 | 采用 | — |
| RFQ | WPForms | Form ID | 字段、按钮、通知 | 采用 | — |

如果无法检查 Theme Options、Pattern 编辑器或后台区块结构，Skill 会停止正式页面生成，只保留组件规划、线框或草稿。

## 发布门禁

正式发布前至少需要确认：

- 首页已经在 Draft、Private 或安全预览环境中完成
- 1440、1024、768、390 四个断点均已检查
- 每个页面只有一个 H1
- H2/H3 层级合理
- 没有整页 Custom HTML 或 Classic Block
- 页面内容中不存在页面级 `<style>`
- 产品分类、应用、质量流程、FAQ 和 RFQ 已记录 Pattern ID
- WPForms 表单前端显示正常
- Header/Footer 不包含演示邮箱、默认 Logo、占位联系方式或无效社媒链接
- 页面底部不存在重复 CTA
- 核心内链有效
- 没有虚构产能、认证、客户、案例或评价
- 后台主要模块能够独立编辑

未通过门禁时，页面必须保持 Draft 或 Private，不得替换正式首页。

## 数据真实性要求

Skill 不会自动编造以下内容：

- 工厂面积
- 年产能
- 员工数量
- 出口国家数量
- 交付周期
- 认证证书
- 客户 Logo
- 客户评价
- 项目案例
- 产品测试结果

缺少真实资料时，应使用中性表达、明确占位符或保持草稿状态。

## WordPress 与工具要求

建议具备：

- 已安装并可访问的 WordPress
- 支持 Gutenberg 的主题
- 可用的 WordPress MCP
- 已登录的 WordPress 后台浏览器
- WPForms 或其他已确认的表单插件
- 产品较多时使用 ACF
- 已配置的 SEO、缓存和安全插件

WordPress MCP 最好支持：

- 页面、文章和自定义文章类型读写
- Gutenberg 原始内容读写
- 可复用 Pattern 读写
- 媒体库读取与上传
- 菜单和站点设置读取
- ACF REST 字段
- WPForms 表单列表

MCP 不具备某项能力时，Skill 会根据规则使用浏览器兜底，或者停止高风险发布操作。

## 自定义与维护

修改 Skill 后建议运行：

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py \
  ~/.codex/skills/build-b2b-wordpress-site
```

更新时重点检查：

- `SKILL.md` 与 `agents/openai.yaml` 的描述是否一致
- 新增 reference 是否已在 `SKILL.md` 中明确引用
- 是否误加入域名、邮箱、API Key、密码、表单 ID 等站点数据
- 是否仍然坚持 MCP 优先和浏览器兜底
- 是否仍然强制后台可视化维护
- 是否保留发布门禁和停止条件

## 当前状态

当前版本已通过 Codex Skill 基础格式校验，并已在真实 WordPress B2B 首页重构流程中进行迭代。

## 许可证

当前仓库尚未添加开源许可证。若计划公开分发、二次开发或商业使用，建议先在仓库中补充合适的 `LICENSE` 文件。
