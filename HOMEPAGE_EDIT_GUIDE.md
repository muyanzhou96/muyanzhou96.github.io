# 个人主页内容修改说明

这份文档说明当前个人主页仓库中各类内容的维护位置。当前项目是 Jekyll / Academic Pages 风格的静态站点，页面内容主要由 Markdown、YAML front matter、Liquid 模板和 `_config.yml` 共同生成。

修改前建议先运行：

```bash
git status --short
```

确认当前工作区状态，避免把无关改动混在一起。不要删除 `resume/` 文件夹，其中保存的是简历源文件和原始照片。

## 1. 项目整体结构说明

- 页面内容：`_pages/`
  - 首页：`_pages/about.md`
  - Publications 页面：`_pages/publications.html`
  - CV 页面：`_pages/cv.md`
  - JSON CV 页面：`_pages/cv-json.md`
  - Projects 页面：`_pages/portfolio.html`
  - Talks / Teaching 等模板页面：`_pages/talks.html`、`_pages/teaching.html`
- 结构化数据：`_data/`
  - 顶部导航：`_data/navigation.yml`
  - 作者信息备份：`_data/authors.yml`
  - JSON CV 数据：`_data/cv.json`
  - UI 文案：`_data/ui-text.yml`
- 模板和局部组件：`_includes/`
  - 作者侧栏：`_includes/author-profile.html`
  - 单篇 publication 渲染：`_includes/archive-single.html`
  - CV 中 publication 渲染：`_includes/archive-single-cv.html`
  - SEO：`_includes/seo.html`
  - 页脚：`_includes/footer.html`
  - 顶部导航模板：`_includes/masthead.html`
- 页面布局：`_layouts/`
  - 默认布局：`_layouts/default.html`
  - 单页布局：`_layouts/single.html`
  - 列表页布局：`_layouts/archive.html`
  - CV 布局：`_layouts/cv-layout.html`
- 发表列表数据：`_publications/`
  - 每篇论文一个 `.md` 文件，使用 YAML front matter 保存标题、venue、date、citation、CCF 标记等。
- 项目经历数据：`_portfolio/`
  - 每个 project 一个 `.md` 文件，由 `_pages/portfolio.html` 渲染。
- 博客文章：`_posts/`
  - 当前未看到主页内容依赖这里。若以后写博客，可以放 Jekyll posts。
- 样式：`assets/css/main.scss` 和 `_sass/`
  - `assets/css/main.scss` 负责导入 `_sass/` 下的主题、布局、组件样式。
- JavaScript：`assets/js/`
  - `assets/js/_main.js` 是源文件，`assets/js/main.min.js` 是压缩后文件。
- 图片和图标：`images/`
  - 当前头像：`images/profile.jpg`
  - favicon：`images/favicon.svg`、`images/favicon.ico`、`images/favicon-*.png`
  - Web manifest：`images/manifest.json`
- 附件：`files/`
  - 可公开下载的 PDF、slides、BibTeX 等应放这里。
  - 当前 `files/bibtex1.bib` 是示例 BibTeX，不是正式 publication 数据源。
- 简历原始资料：`resume/`
  - 当前有 `resume/main-en.tex`、`resume/main-en.pdf`、`resume/person2.jpg` 等。
  - `resume/` 在 `_config.yml` 第 195-196 行附近被排除，不会直接进入生成站点。
- 网站配置：`_config.yml`
  - 站点标题、作者信息、社交链接、SEO 描述、collections、插件、排除目录等都在这里。
- GitHub Actions：`.github/workflows/`
  - `scrape_talks.yml`：talk map notebook 自动执行流程。
  - `bad-pr.yml`：模板遗留的 PR 清理 workflow。
- 本地依赖：
  - Ruby/Jekyll：`Gemfile`
  - Python notebook：`requirements.txt`
  - JS assets：`package.json`

## 2. 首页各部分内容在哪里修改

#### 首页个人简介 / Biography

- 显示位置：首页正文最上方。
- 修改文件：`_pages/about.md`
- 大致行号：第 11-15 行附近。
- 搜索关键词：`I am a postdoctoral researcher`
- 修改方式：直接修改 Markdown 正文。
- 注意事项：
  - 如果要添加导师链接，使用 Markdown 链接：`[Prof. Name](https://example.com)`。
  - 不要把 URL 裸露显示在正文中。
  - 主页 front matter 的短描述在 `_pages/about.md` 第 4 行，也可同步更新。

#### 头像

- 显示位置：页面左侧作者侧栏。
- 修改文件：`_config.yml`
- 大致行号：第 28 行附近，字段是 `author.avatar`。
- 当前路径：`images/profile.jpg`
- 搜索关键词：`avatar`
- 渲染模板：`_includes/author-profile.html` 第 9-14 行附近。
- 修改方式：
  - 替换 `images/profile.jpg`，保持文件名不变；或
  - 放入新文件，例如 `images/profile-new.jpg`，再把 `_config.yml` 第 28 行改成 `profile-new.jpg`。
- 注意事项：头像路径默认会拼接 `/images/`，不要写成 `images/profile.jpg`，只写文件名即可。

#### 姓名

- 首页标题：`_pages/about.md` 第 3 行，字段 `title`。
- 全站标题和默认作者名：`_config.yml` 第 12、14、29 行附近。
- 作者数据备份：`_data/authors.yml` 第 3-4 行附近。
- 搜索关键词：`Yanzhou Mu`
- 注意事项：修改姓名时建议同步修改以上三个文件，否则页面标题、侧栏和结构化信息可能不一致。

#### 职业身份

- 首页正文：`_pages/about.md` 第 11 行附近。
- 侧栏简介：`_config.yml` 第 31 行附近，字段 `author.bio`。
- 作者数据备份：`_data/authors.yml` 第 6 行附近。
- SEO 描述：`_config.yml` 第 15 行附近。
- 搜索关键词：`Postdoctoral researcher`

#### 邮箱

- 首页 Contact：`_pages/about.md` 第 74-77 行附近。
- 侧栏邮箱：`_config.yml` 第 35 行附近。
- 作者数据备份：`_data/authors.yml` 第 5 行附近。
- 搜索关键词：`mailto:`
- 注意事项：邮箱正文和 `mailto:` 链接要保持一致。

#### GitHub / Google Scholar / LinkedIn 等社交链接

- 修改文件：`_config.yml`
- 大致行号：
  - Google Scholar：第 40 行，字段 `googlescholar`
  - GitHub：第 56 行，字段 `github`
  - LinkedIn：第 71 行，字段 `linkedin`
  - ORCID：第 43 行，字段 `orcid`
  - 其他社交平台：第 37-85 行附近
- 渲染模板：`_includes/author-profile.html`
  - Google Scholar：第 47-49 行附近
  - GitHub：第 88-90 行附近
  - LinkedIn：第 129 行以后
- 修改方式：在 `_config.yml` 中填写用户名或 URL，空字段不会显示。
- 注意事项：
  - `github` 填用户名，例如 `muyanzhou96`，模板会自动生成 `https://github.com/...`。
  - `googlescholar`、`orcid` 等字段通常填完整 URL。

#### News 栏目

- 显示位置：首页 Biography 下方。
- 修改文件：`_pages/about.md`
- 大致行号：第 17-24 行附近。
- 搜索关键词：`News`
- 修改方式：直接修改 Markdown 列表。
- 注意事项：当前 News 是硬编码在首页中，没有独立 `_data/news.yml`，也没有自动截断逻辑。

#### Research Interests / 研究兴趣

- 显示位置：首页 `Research Areas`。
- 修改文件：`_pages/about.md`
- 大致行号：第 26-33 行附近。
- 搜索关键词：`Research Areas`
- 修改方式：修改 Markdown 列表项。

#### Publications 简要展示

- 当前首页未找到明确的 Publications 简要展示区块。
- 完整发表列表在：`_pages/publications.html` 和 `_publications/`。
- 如果以后想在首页加精选论文，建议在 `_pages/about.md` 的 `Research Areas` 后或 `Selected Projects` 前新增 Markdown 区块，或用 Liquid 从 `_publications/` 读取。

#### Service / Academic Service 栏目

- 显示位置：首页 `Service` 区域。
- 修改文件：`_pages/about.md`
- 大致行号：第 50-72 行附近。
- 搜索关键词：`Service`
- 修改方式：直接修改 Markdown 小标题和列表。

#### 简历下载链接

- 当前 `/cv-json/` 页面支持 PDF 下载按钮，但 `site.cv_pdf` 为空。
- 控制字段：`_config.yml` 第 21 行附近，字段 `cv_pdf`。
- 下载按钮模板：`_pages/cv-json.md` 第 15-23 行附近。
- 当前 PDF 原始文件：`resume/main-en.pdf`，但 `resume/` 被排除，不会发布。
- 建议公开简历路径：复制公开版 PDF 到 `files/Yanzhou_Mu_CV.pdf`，然后设置：

```yaml
cv_pdf: /files/Yanzhou_Mu_CV.pdf
```

- 注意事项：公开简历前检查 PDF 中是否包含不适合公开的信息。

#### 页面底部信息

- 修改文件：`_includes/footer.html`
- 大致行号：第 3-24 行附近。
- 显示内容：
  - GitHub / Feed 链接：第 3-20 行附近
  - Copyright 和站点更新时间：第 22-24 行附近
- 站点名来源：`_config.yml` 第 14 行 `name` 或第 12 行 `title`。
- 搜索关键词：`Site last updated`

## 3. Publications / 发表列表如何修改

#### 数据存放位置

- 发表列表数据：`_publications/*.md`
- 发表列表页面：`_pages/publications.html`
- 排序辅助模板：`_includes/publications-by-fallback-order.html`
- 单篇列表入口模板：`_includes/archive-single.html`
- Publications 三行列表模板：`_includes/publication-single.html`
- CV 中的 publication 渲染模板：`_includes/archive-single-cv.html`
- 分类标题配置：`_config.yml` 第 87-94 行附近，字段 `publication_category`

#### 每篇论文的标题、作者、venue、年份在哪里改

每篇论文一个 Markdown 文件，主要内容在文件开头的 YAML front matter。例子：

- `_publications/2026-01-01-llm-centric-challenges.md`
- 大致行号：第 1-11 行附近

字段说明：

- `title`：论文标题，第 2 行附近。
- `category`：分类，例如 `manuscripts` 或 `conferences`，第 4 行附近。
- `ccf`：CCF 标记，例如 `"A"`，第 5 行附近。
- `sortorder`：手动排序值，整数越大越靠前；只影响列表顺序，不会显示在网页上。
- `status`：状态，例如 `"Major revision"`，如果有的话在第 6 行附近。
- `date`：排序日期和显示年份，第 8-9 行附近。
- `venue`：期刊或会议名称，第 9-10 行附近。
- `citation`：作者列表和完整引用，第 10-11 行附近。
- `authors`：可选字段。如果填写，Publications 三行列表的第二行优先使用它；如果不填，模板会尝试从 `citation` 中截取作者列表。
- `venue_short`：可选字段。如果填写，Publications 三行列表第一行优先使用它；如果不填，模板会尝试从 `venue` 中提取缩写。

#### 我的名字加粗在哪里实现

- 主 publication 页面：`_includes/publication-single.html`
- 大致行号：第 55-64 行附近。
- 代码逻辑：渲染时把 `Yanzhou Mu` 和 `沐燕舟` 替换成 `<strong>...</strong>`。
- `_includes/archive-single.html` 第 20-24 行附近会判断 `post.collection == 'publications'`，然后调用 `_includes/publication-single.html`。
- CV publication 页面：`_includes/archive-single-cv.html`
- 大致行号：第 15-18 行附近。
- 注意事项：
  - 通常不需要在每个 `_publications/*.md` 文件中手动写 `<strong>`。
  - 如果以后姓名有缩写写法，需要在这两个模板中扩展替换规则。

#### CCF-A 排序或标记在哪里实现

- 标记字段：每篇 `_publications/*.md` 的 front matter 中添加 `ccf: "A"`。
- 显示 CCF 标记：`_includes/publication-single.html` 第 33-53 行附近。
- 排序逻辑入口：`_pages/publications.html` 第 13-19 行附近。
- fallback 排序逻辑：`_includes/publications-by-fallback-order.html` 第 1-77 行附近。
- 当前 fallback 逻辑：
  - 同一个 `sortorder` 内先显示 `ccf: "A"` 的论文。
  - 非 CCF-A 论文再按 `_config.yml` 中 `publication_category` 的分类顺序显示。
  - 同组内按 `date` 倒序。

### 如何使用 sortorder 手动调整 Publications 顺序

`sortorder` 是 Publications 列表的手动排序字段。它写在每篇论文的 `_publications/*.md` front matter 中，只控制 `/publications/` 列表顺序，不会显示在网页正文里。

示例：

```yaml
sortorder: 1000
```

请写成 YAML 整数，不要加引号，例如不要写成 `sortorder: "1000"`。

当前排序规则：

1. 先按 `sortorder` 降序，数值越大越靠前。
2. 没有 `sortorder` 的论文排在所有有 `sortorder` 的论文后面。
3. 如果多篇论文 `sortorder` 相同，则使用原 fallback 规则：CCF-A 优先，再按 publication category，最后按 `date` 倒序。

修改位置：

- 文件位置：`_publications/`
- 大致行号：每个 publication 文件第 1-12 行附近
- 搜索关键词：论文标题、`sortorder:`、`date:`
- 示例文件：`_publications/2026-06-18-cipihunter.md`
- 示例字段：`sortorder: 1000`

使用建议：

- 新增论文时建议填写 `sortorder`，并使用间隔较大的整数。
- 如果当前最高 `sortorder` 是 `1000`，想让新论文排到最前，可以设置为 `1010` 或 `1100`。
- 如果想插入在 `1000` 和 `990` 两篇论文之间，可以设置为 `995`。
- 如果只是想调整顺序，优先改 `sortorder`，不要改论文标题、作者、venue、citation 或文件名。
- 不要修改 `_site/` 中的生成 HTML；重新 build 后 `_site/` 会被覆盖。

修改后验证：

```bash
bundle exec jekyll clean
bundle exec jekyll build
```

然后打开 `/publications/` 检查顺序。也可以在构建产物中确认 `sortorder` 没有显示在 Publications 页面：

```bash
grep -n "sortorder" _site/publications/index.html || true
```

注意：如果全站搜索 `_site`，可能会命中这份维护文档自身；判断网页是否泄露 `sortorder` 时，以 `_site/publications/index.html` 为准。

### 如何新增一篇 Publication

新增文献应该放在 `_publications/` 目录下。当前正式发表列表来自 `_publications/*.md`，不是 BibTeX、YAML 或 JSON。

建议复制一个已有 publication 文件作为模板：

- CCF-A 会议论文可参考：`_publications/2026-06-18-cipihunter.md`
- CCF-A 期刊论文可参考：`_publications/2026-01-01-llm-centric-challenges.md`
- 普通会议论文可参考：`_publications/2019-01-01-asttoken2vec.md`
- 普通期刊论文可参考：`_publications/2021-01-02-heterogeneous-defect-prediction.md`

新文件命名建议：

```text
YYYY-MM-DD-short-title.md
```

命名规则：

- `YYYY-MM-DD` 建议和 front matter 中的 `date` 一致。
- `short-title` 使用英文小写、数字和连字符，不要使用空格。
- 文件名中不要使用中文、斜杠或特殊符号。
- `date` 会影响 Publications 列表排序。
  如果使用 `sortorder`，主要顺序由 `sortorder` 控制，`date` 只作为 fallback 和显示年份使用。

当前三行 Publications 列表的字段来源：

- 第一行标题：`title`。
- 第一行括号：优先使用 `venue_short`；如果没有，`_includes/publication-single.html` 第 8-31 行附近会尝试从 `venue` 自动提取缩写。CCF 信息来自 `ccf`。
- 第二行作者列表：优先使用 `authors`；如果没有，`_includes/publication-single.html` 第 55-64 行附近会尝试从 `citation` 中截取作者列表，并自动加粗 `Yanzhou Mu` 或 `沐燕舟`。
- 第三行完整 venue：使用 `venue` 和 `date` 年份；如果有 `status`，也会追加显示。

字段建议：

- 必填：`title`、`collection: publications`、`category`、`permalink`、`date`、`venue`、`citation`。
- 推荐填写：`sortorder`、`venue_short`、`authors`。`sortorder` 控制手动排序，`venue_short` 和 `authors` 可以让三行列表更稳定。
- 可选：`ccf`、`status`、`excerpt`、`paperurl`、`slidesurl`、`bibtexurl`。
- 当前模板没有使用 `year` 字段；年份来自 `date`。

新增论文模板如下，格式符合当前项目的 Markdown collection 文件：

```markdown
---
title: "Paper Title"
collection: publications
category: conferences
ccf: "A"
sortorder: 1000
permalink: /publication/YYYY-MM-DD-short-title
excerpt: "One-sentence summary of this paper."
date: YYYY-MM-DD
venue: "Full Conference or Journal Name"
venue_short: "SHORT"
authors: "Author A, Yanzhou Mu, Author C"
citation: "Author A, Yanzhou Mu, Author C. Paper Title. Full Conference or Journal Name, YYYY."
---

This publication is listed from a verified source.
```

填写说明：

- 如果不是 CCF-A 论文，不要写 `ccf: "A"`。
- `sortorder` 建议用整数，数值越大越靠前。新增论文时可以选择当前相邻论文之间的空档值。
- 如果无法确认 `venue_short`，可以先不写；但三行列表第一行可能只能使用模板从 `venue` 推断出的缩写。
- 如果填写 `authors`，保持作者原始顺序。可以写 `Yanzhou Mu`，模板会自动加粗；也可以手动写 `<strong>Yanzhou Mu</strong>`，但不推荐混用。
- 如果是 major revision，可以加：

```yaml
status: "Major revision"
```

新增后验证：

- 本地构建：`bundle exec jekyll build`
- 本地预览：`bundle exec jekyll serve`
- 页面路径：`/publications/`
- 搜索关键词：论文标题、`permalink` 中的 slug、`venue_short` 或 `citation` 中的作者名。
- 检查点：标题链接是否能打开、作者列表中我的名字是否加粗、CCF 是否只在已确认条目中显示、venue 是否显示完整。

常见错误：

- 忘记写 `collection: publications`，导致 Jekyll 不把它当作 publication。
- `permalink` 和已有论文重复。
- `date` 格式不是 `YYYY-MM-DD`。
- YAML front matter 没有用开头和结尾的 `---` 包住。
- 冒号后缺少空格，例如写成 `date:2026-06-18`。
- `sortorder` 加了引号或写成非数字文本，导致排序结果不符合预期。
- 标题或 citation 中有冒号、单引号等字符时没有加引号。
- 忘记重新 build，导致页面仍是旧内容。
- 只修改 `_site/` 生成文件，而没有修改 `_publications/*.md` 源文件。

#### 删除论文

- 删除对应的 `_publications/*.md` 文件即可。
- 不要只删除 `citation`，否则页面可能仍显示空条目。
- 删除前确认没有其他页面或 CV 引用该条目。

#### BibTeX / Markdown / YAML 说明

- 当前网站正式发表列表来自 `_publications/*.md`，不是 BibTeX。
- `files/bibtex1.bib` 是示例文件，不是正式数据源。
- `markdown_generator/publications.tsv` 和相关 notebook / script 是生成工具或模板遗留，不是当前完整发表列表的权威来源。

## 4. News 栏目如何修改

- News 存放位置：`_pages/about.md`
- 大致行号：第 17-24 行附近。
- 搜索关键词：`News`
- 当前实现：硬编码 Markdown 列表，不是独立数据文件。
- 当前显示数量：手动维护为 5 条，没有自动“只显示最新五条”的代码。

#### 新增一条 News

在 `News` 标题下新增一行，例如：

```markdown
* 2026.06 🎉 Our paper is accepted to TOSEM.
```

#### 删除一条 News

删除对应的 `* YYYY.MM ...` 那一行即可。

#### 调整 News 顺序

- 手动按时间倒序排列。
- 日期格式统一使用 `YYYY.MM`，例如 `2026.05`。
- 同一个月份有多条时，把更重要的放前面。

#### emoji

- 可以保留 emoji，例如 `🎉`。
- 建议 emoji 前后保留空格，让正文易读。

## 5. Service / Academic Service 如何修改

- Service 存放位置：`_pages/about.md`
- 大致行号：第 50-72 行附近。
- 搜索关键词：`Service`

#### Journal Reviewer

- 位置：`_pages/about.md` 第 53-56 行附近。
- 搜索关键词：`Journal Reviewer`
- 新增示例：

```markdown
* IEEE Transactions on Software Engineering (TSE)
```

#### Conference Service / PC Member

- 位置：`_pages/about.md` 第 58-68 行附近。
- 搜索关键词：`Conference Service / Reviewing`
- PC Member 新增示例：

```markdown
* 2027: Program Committee Member, ASE
```

#### Shadow PC

- 当前位置：`_pages/about.md` 第 64 行附近。
- 新增示例：

```markdown
* 2027: Shadow PC, ICSE
```

#### Co-reviewer

- 当前位置：`_pages/about.md` 第 65-68 行、第 72 行附近。
- 新增示例：

```markdown
* 2027: Co-reviewer, ISSTA
```

#### 注意事项

- 不要把 `Co-reviewer` 写成 `Program Committee Member`。
- 不要把 `Shadow PC` 写成正式 `Program Committee Member`。
- 如果角色不确定，先写中性表述或暂不添加。

## 6. 个人基本信息如何修改

| 内容 | 文件路径 | 大致行号 | 搜索关键词 | 注意事项 |
| --- | --- | --- | --- | --- |
| 网站作者姓名 | `_config.yml` | 第 12、14、29 行 | `Yanzhou Mu` | 同步 `_pages/about.md` 第 3 行和 `_data/authors.yml` 第 3-4 行 |
| 网站标题 | `_config.yml` | 第 12 行 | `title` | 影响 `<title>` 和 Open Graph |
| 网站描述 | `_config.yml` | 第 15 行 | `description` | 影响默认 SEO description |
| 首页 description | `_pages/about.md` | 第 4 行 | `description` | 首页会优先使用 page description |
| 邮箱 | `_config.yml`、`_pages/about.md`、`_data/authors.yml` | `_config.yml` 第 35 行；`_pages/about.md` 第 77 行；`_data/authors.yml` 第 5 行 | `email` 或 `mailto:` | 三处建议同步 |
| 头像 | `_config.yml`、`images/` | `_config.yml` 第 28 行 | `avatar` | 当前头像文件是 `images/profile.jpg` |
| 简历文件 | `_config.yml`、`files/`、`_pages/cv-json.md` | `_config.yml` 第 21 行；`_pages/cv-json.md` 第 15-23 行 | `cv_pdf` | `resume/` 被排除，公开 PDF 建议放 `files/` |
| Google Scholar | `_config.yml` | 第 40 行 | `googlescholar` | 填完整 URL |
| GitHub | `_config.yml` | 第 56 行 | `github` | 填用户名，模板自动生成链接 |
| LinkedIn | `_config.yml` | 第 71 行 | `linkedin` | 填用户名，模板自动生成链接 |
| ORCID | `_config.yml` | 第 43 行 | `orcid` | 填完整 URL 或模板支持的值 |
| SEO title | `_includes/seo.html`、`_config.yml`、页面 front matter | `_includes/seo.html` 第 9-21 行；`_config.yml` 第 12-15 行 | `seo_title` | 通常改 `_config.yml` 和页面 `title`，不要直接改模板 |
| SEO description | `_includes/seo.html`、`_config.yml`、页面 front matter | `_includes/seo.html` 第 23-30 行；`_config.yml` 第 15 行 | `seo_description` | 页面 description 优先于站点 description |
| favicon / 网站图标 | `images/favicon.svg`、`images/favicon.ico`、`images/favicon-*.png`、`images/manifest.json` | `favicon.svg` 第 1-4 行；`manifest.json` 第 11-16 行 | `favicon` | 替换图标时保持路径或同步 manifest |
| 导航栏菜单 | `_data/navigation.yml` | 第 10-18 行 | `main:` | 修改后检查顶部导航 |

## 7. 页面导航如何修改

- 导航栏数据文件：`_data/navigation.yml`
- 大致行号：第 10-18 行附近。
- 搜索关键词：`main:`

#### 新增一个导航入口

在 `main:` 下添加：

```yaml
  - title: "News"
    url: /news/
```

如果新增的是独立页面，还需要在 `_pages/` 下创建页面文件，例如 `_pages/news.md`：

```markdown
---
layout: archive
title: "News"
permalink: /news/
author_profile: true
---

页面内容写这里。
```

#### 删除一个导航入口

删除 `_data/navigation.yml` 中对应的两行 `title` 和 `url`。

#### 调整导航顺序

直接调整 `_data/navigation.yml` 中 `main:` 下各条目的顺序。

#### 新增页面需要注意

- `_config.yml` 第 166-169 行 include 了 `_pages`，所以 `_pages/` 下页面会被 Jekyll 处理。
- 页面必须有 front matter，也就是文件开头的 `---` 区块。
- `permalink` 要和导航里的 `url` 对上。

### 如何维护 Students 页面

#### Students 页面在哪里

- Students 页面文件：`_pages/students.md`
- 导航栏配置文件：`_data/navigation.yml`
- 页面 URL / permalink：`/students/`
- 页面 front matter：`_pages/students.md` 第 1-6 行附近
- 页面标题：修改 `_pages/students.md` 第 3 行附近的 `title: "Students"`
- 导航栏文字：修改 `_data/navigation.yml` 第 14 行附近的 `title: "Students"`
- 导航栏 URL：修改 `_data/navigation.yml` 第 15 行附近的 `url: /students/`
- 搜索关键词：`Current Students`、`Alumni`、`url: /students/`

当前 Students 页面有两个分类：

- `## Current Students`：`_pages/students.md` 第 8 行附近
- `## Alumni`：`_pages/students.md` 第 20 行附近

#### 如何新增 Current Student

在 `_pages/students.md` 的 `## Current Students` 标题下面新增一条 Markdown 列表项。建议放在当前学生列表中合适的位置，例如按入组时间、学生类型或你想展示的顺序手动排列。

推荐格式：

```markdown
* **学生姓名**, Ph.D. student, co-supervised with Prof. XXX, Sep. 2026–present.
```

如果没有共同指导老师：

```markdown
* **学生姓名**, undergraduate intern, May 2026–present.
```

如果学生还没有正式开始、但已经确定入组：

```markdown
* **学生姓名**, M.S. student, co-supervised with Prof. XXX, starting Sep. 2026.
```

常用身份写法：

- `Ph.D. student`
- `M.S. student`
- `undergraduate intern`

时间格式建议：

- 已开始：`Sep. 2022–present`
- 未来开始：`starting Sep. 2026`
- 月份缩写保持一致，例如 `Jan.`、`May`、`Jul.`、`Aug.`、`Sep.`、`Oct.`

#### 如何把 Current Student 移到 Alumni

1. 在 `_pages/students.md` 的 `## Current Students` 下找到该学生条目。
2. 剪切或删除这条 current student 记录。
3. 粘贴到 `## Alumni` 标题下面。
4. 将学生身份改成毕业身份，例如 `M.S.` 或 `undergraduate intern`。
5. 将时间范围改成毕业年份，例如 `graduated in 2026`。
6. 如果知道毕业去向，追加 `Currently ...`；不知道去向时不要编造。

有去向的写法：

```markdown
* **学生姓名**, M.S., co-supervised with Prof. XXX, graduated in 2026. Currently at XXX.
```

没有去向的写法：

```markdown
* **学生姓名**, M.S., co-supervised with Prof. XXX, graduated in 2026.
```

如果去向是继续读博，可以写：

```markdown
* **学生姓名**, M.S., graduated in 2026. Currently a Ph.D. student at XXX University.
```

#### 如何新增新的学生分类

如果以后想新增 `Visiting Students`、`Undergraduate Interns`、`Collaborating Students`、`Former Interns` 等页面内部栏目，只需要在 `_pages/students.md` 中增加一个二级 Markdown 标题和对应列表。

示例：

```markdown
## Visiting Students

* **学生姓名**, visiting student, Jan. 2027–Jun. 2027.
```

注意：

- 新增页面内部栏目不需要修改导航栏。
- 只有新增独立页面时，才需要修改 `_data/navigation.yml`。
- 新栏目建议继续使用 `##`，保持和 `Current Students`、`Alumni` 同级。

#### 如何修改已有学生信息

在 `_pages/students.md` 中搜索学生姓名，然后直接修改对应列表项：

- 姓名：修改 `**姓名**` 中的文字。
- 学位类型：修改 `Ph.D. student`、`M.S. student`、`undergraduate intern` 等身份字段。
- 共同指导老师：修改 `co-supervised with Prof. XXX`。
- 起止时间：修改 `Sep. 2022–present`、`starting Sep. 2026` 或 `graduated in 2026`。
- 当前去向：修改 `Currently ...` 后面的文字。
- 拼写错误：直接修正对应单词，例如 `Octorber` 应改为 `Oct.`。

不要修改 `_site/` 下的构建产物，也不要只改浏览器里看到的 HTML。应该修改源文件 `_pages/students.md`，然后重新构建。

#### 推荐格式规范

- 姓名加粗：`**Student Name**`
- 博士生：`Ph.D. student`
- 硕士生：`M.S. student`
- 本科实习生：`undergraduate intern`
- 时间范围：`Sep. 2022–present`
- 未来入组：`starting Sep. 2026`
- 毕业年份：`graduated in 2026`
- 去向：`Currently at ...` 或 `Currently a Ph.D. student at ...`
- 共同指导：`co-supervised with Prof. XXX`
- 不要混用 `~`、`From`、`Present`、`present` 等不统一格式。

#### 修改后如何验证

本项目是 Jekyll / academicpages 风格站点。修改 Students 页面后建议运行：

```bash
bundle exec jekyll clean
bundle exec jekyll build
bundle exec jekyll serve
```

本地预览 URL：

```text
http://localhost:4000/students/
```

检查内容：

- 顶部导航栏是否仍显示 `Students`。
- `Students` 导航是否打开 `/students/`。
- `Current Students` 和 `Alumni` 是否正常渲染成标题。
- 每条学生信息是否是 Markdown 列表。
- 学生姓名是否加粗。
- 没有把学生信息误写到 Service、Publications 或 `_site/`。

#### 常见错误

- 改了 `_site/` 里的生成文件，下次 build 后被覆盖。
- 忘记在学生姓名两边加 `**`。
- 把 `co-reviewer`、`PC Member` 等 Service 内容误放到 Students。
- 日期格式不统一，例如混用 `Present` 和 `present`。
- 月份拼写错误，例如 `Octorber` 应写为 `Oct.`。
- 新增独立 Students 子页面后忘记更新 `_data/navigation.yml`。
- Markdown 列表缩进错误，导致列表渲染异常。

## 8. 图片、头像、PDF 简历等资源如何替换

#### 头像

- 当前头像显示文件：`images/profile.jpg`
- 配置位置：`_config.yml` 第 28 行，`author.avatar: "profile.jpg"`
- 渲染模板：`_includes/author-profile.html` 第 9-14 行。
- 推荐做法：
  - 直接替换 `images/profile.jpg`；或
  - 新增 `images/profile-2026.jpg`，然后改 `_config.yml` 第 28 行为 `profile-2026.jpg`。

#### 简历 PDF

- 当前原始 PDF：`resume/main-en.pdf`
- 公开附件推荐位置：`files/Yanzhou_Mu_CV.pdf`
- 配置位置：`_config.yml` 第 21 行，字段 `cv_pdf`
- 下载按钮位置：`_pages/cv-json.md` 第 15-23 行。
- 注意事项：
  - `resume/` 在 `_config.yml` 第 195-196 行附近被排除，不适合直接作为公开下载路径。
  - 公开 PDF 前先移除不适合公开的信息。

#### favicon / 网站图标

- SVG 图标：`images/favicon.svg`
- PNG 图标：`images/favicon-192x192.png`、`images/favicon-512x512.png` 等。
- ICO 图标：`images/favicon.ico`
- manifest：`images/manifest.json` 第 11-16 行。
- 替换时建议保留同名文件，避免同步修改多处路径。

#### 其他附件

- 论文 PDF、slides、BibTeX 等公开资源建议放在 `files/`。
- 在 `_publications/*.md` 中可以使用字段：
  - `paperurl`
  - `slidesurl`
  - `bibtexurl`
- `_includes/archive-single.html` 第 60-85 行附近会根据这些字段自动显示下载链接。

#### 避免路径导致构建失败

- Jekyll 内部路径建议以 `/files/...` 或 `/images/...` 开头。
- `_config.yml` 中的 `author.avatar` 只写图片文件名，因为模板会自动拼接 `/images/`。
- 修改路径后运行 `bundle exec jekyll build` 检查。

## 9. 样式如何调整

- 全站样式入口：`assets/css/main.scss`
  - 大致行号：第 11-43 行，负责导入 `_sass/` 文件。
- 主题颜色：`_sass/theme/`
  - 主题选择在 `_config.yml` 第 11 行，字段 `site_theme`。
- 页面布局样式：`_sass/layout/`
  - `_sass/layout/_page.scss`
  - `_sass/layout/_archive.scss`
  - `_sass/layout/_sidebar.scss`
  - `_sass/layout/_masthead.scss`
  - `_sass/layout/_footer.scss`
- Publications 样式：
  - 主要由 `_sass/layout/_archive.scss` 控制 archive item。
  - 内容结构由 `_includes/archive-single.html` 控制。
- News / Service 样式：
  - 当前没有单独样式，使用 Markdown 标题和列表的默认样式。
  - 若只是改文字，不需要改 CSS。
- JavaScript 源文件：`assets/js/_main.js`
  - 主题切换和 Plotly 逻辑在第 1-80 行附近。
- 不建议随意修改：
  - `assets/js/main.min.js`，这是压缩产物。
  - `_sass/vendor/`，这是第三方/vendor 样式。
  - `_includes/seo.html`，除非明确要改 SEO 模板逻辑。

## 10. 本地预览和构建命令

#### Ruby / Jekyll 依赖

依赖文件：`Gemfile` 第 1-13 行。

安装依赖：

```bash
bundle install
```

本地预览：

```bash
bundle exec jekyll serve -l -H localhost
```

然后打开：

```text
http://localhost:4000
```

本地构建：

```bash
bundle exec jekyll build
```

注意：如果本机 Ruby 环境报 `eventmachine`、`ruby/config.h`、OpenSSL 或 Command Line Tools 相关错误，优先检查 Ruby 开发环境，而不是先改页面内容。

#### Python notebook / talkmap

依赖文件：`requirements.txt` 第 1-5 行。

安装依赖：

```bash
python -m pip install -r requirements.txt
```

执行 talkmap notebook：

```bash
python -m jupyter nbconvert --to notebook --execute talkmap.ipynb --output talkmap_out.ipynb
```

GitHub Actions 中对应流程在 `.github/workflows/scrape_talks.yml`：

- Python 版本：第 31-35 行，当前是 Python 3.11。
- 安装依赖：第 37-42 行。
- 执行 notebook：第 43-46 行。
- 自动提交 talkmap 结果：第 48-55 行。
- 只有 `_talks` 中存在 talk 文件时才运行，判断逻辑在第 21-29 行。

#### JavaScript assets

依赖和命令在 `package.json`：

- 依赖：第 24-32 行。
- 脚本：第 34-37 行。

安装依赖：

```bash
npm install
```

重新压缩 JS：

```bash
npm run build:js
```

当前没有 `npm run build` 脚本，只有 `build:js`。

## 11. 修改前后的检查清单

每次修改主页后建议检查：

- [ ] `git status --short` 中只包含本次相关文件。
- [ ] 没有误删 `resume/` 文件夹。
- [ ] 首页能打开，Biography、News、Research Areas、Service 显示正常。
- [ ] 头像能显示，路径仍指向 `images/` 下存在的文件。
- [ ] 邮箱链接能点击，`mailto:` 地址正确。
- [ ] 如果启用了简历下载，PDF 路径能打开并且不在 `resume/` 排除目录下。
- [ ] Publications 页面能显示全部论文。
- [ ] `_publications/` 文件数没有被误删。
- [ ] `Yanzhou Mu` / `沐燕舟` 在 publication citation 中仍然加粗。
- [ ] Publications 页面顺序符合 `sortorder` 降序；相同 `sortorder` 内仍按 CCF-A、分类和 `date` fallback 排序。
- [ ] News 只保留想展示的最新条目，并按 `YYYY.MM` 倒序排列。
- [ ] Service 中 `Program Committee Member`、`Shadow PC`、`Co-reviewer` 身份写准确。
- [ ] 顶部导航链接能打开。
- [ ] 没有模板作者信息残留在公开页面中。
- [ ] 没有把手机号、详细地址、出生日期等敏感信息加入公开页面。
- [ ] 能运行 `git diff --check`，没有多余空白或语法异常。
- [ ] 能运行 `bundle exec jekyll build`，或明确知道失败来自本地 Ruby 环境。

## 12. 常见修改场景速查表

| 想修改的内容 | 应该修改的文件 | 大致行号 / 搜索关键词 | 修改方式 | 注意事项 |
| --- | --- | --- | --- | --- |
| 修改首页简介 | `_pages/about.md` | 第 11-15 行；搜索 `I am a postdoctoral researcher` | 直接改 Markdown 正文 | 链接用 Markdown，不要裸露 URL |
| 修改头像 | `_config.yml`、`images/` | `_config.yml` 第 28 行；搜索 `avatar` | 替换 `images/profile.jpg` 或改文件名 | `avatar` 只写文件名 |
| 修改邮箱 | `_pages/about.md`、`_config.yml`、`_data/authors.yml` | about 第 77 行；config 第 35 行；authors 第 5 行 | 同步改邮箱和 `mailto:` | 三处保持一致 |
| 修改导师链接 | `_pages/about.md` | 第 11-13 行；搜索导师姓名 | 使用 `[姓名](URL)` | 不要在正文裸露 URL |
| 新增 News | `_pages/about.md` | 第 17-24 行；搜索 `News` | 加一行 `* YYYY.MM ...` | 手动保持倒序 |
| 删除 News | `_pages/about.md` | 第 17-24 行 | 删除对应列表项 | 当前没有自动截断 |
| 新增论文 | `_publications/` | 参考任一 `_publications/*.md` | 新建 `YYYY-MM-DD-title.md` | front matter 必须完整 |
| 修改论文作者 | `_publications/*.md` | 搜索论文标题或 `citation:` | 修改 `citation` 字段 | 保持作者顺序 |
| 修改论文排序 | `_publications/*.md`、`_pages/publications.html`、`_includes/publications-by-fallback-order.html` | 搜索 `sortorder:`；publications 第 13-20 行 | 优先改 `sortorder`，数值越大越靠前 | 不要为了排序改标题、作者、venue 或 `_site/` |
| 修改 CCF-A 标记 | `_publications/*.md` | 搜索 `ccf:` | 添加或删除 `ccf: "A"` | 未确认的论文不要强行标 A |
| 新增 Service | `_pages/about.md` | 第 50-72 行；搜索 `Service` | 在对应类别加列表项 | 不要混淆 PC、Shadow PC、Co-reviewer |
| 新增 Current Student | `_pages/students.md` | 搜索 `Current Students` | 在标题下新增 `* **Name**, ...` 列表项 | 保持姓名加粗和日期格式统一 |
| 将学生移动到 Alumni | `_pages/students.md` | 搜索学生姓名和 `Alumni` | 从 Current Students 移到 Alumni，并改成 `graduated in YYYY` | 不知道去向时不要编造 |
| 新增 Students 子栏目 | `_pages/students.md` | 搜索 `Current Students` 或 `Alumni` | 新增 `## Visiting Students` 等二级标题和列表 | 页面内部栏目通常不用改导航 |
| 修改学生毕业去向 | `_pages/students.md` | 搜索学生姓名或 `Currently` | 修改 `Currently ...` 后面的文字 | 不要改 `_site/` 生成文件 |
| 修改 Students 导航栏文字 | `_data/navigation.yml` | 第 14-15 行；搜索 `Students` 或 `/students/` | 修改对应 `title`，必要时同步页面 `title` | `url` 必须和页面 permalink 对上 |
| 修改简历 PDF | `files/`、`_config.yml`、`_pages/cv-json.md` | config 第 21 行；cv-json 第 15-23 行 | PDF 放 `files/`，设置 `cv_pdf` | `resume/` 不公开 |
| 修改导航栏 | `_data/navigation.yml` | 第 10-18 行；搜索 `main:` | 添加/删除/移动条目 | 新页面需有 front matter 和 permalink |
| 修改网站标题 | `_config.yml`、页面 front matter | config 第 12 行；about 第 3 行 | 修改 `title` | 影响 SEO 和浏览器标题 |
| 修改 SEO 描述 | `_config.yml`、`_pages/about.md` | config 第 15 行；about 第 4 行 | 修改 `description` | 页面 description 优先 |
| 修改 favicon | `images/favicon.svg`、`images/favicon.ico`、`images/favicon-*.png`、`images/manifest.json` | favicon.svg 第 1-4 行；manifest 第 11-16 行 | 替换同名文件最稳妥 | 同步 manifest 图标路径 |
| 本地预览 | `Gemfile` | README 第 7-21 行也有命令 | `bundle exec jekyll serve -l -H localhost` | 改 `_config.yml` 后重启服务 |
| 本地构建 | `Gemfile` | 搜索 `bundle exec jekyll build` | `bundle exec jekyll build` | native gem 报错先查 Ruby 环境 |

## 13. 目前未找到明确位置的内容

- 首页没有独立的 Publications 简要展示区块；完整列表在 `/publications/`。
- 当前没有独立 `_data/news.yml`；News 写死在 `_pages/about.md`。
- 当前没有独立 `_data/service.yml`；Service 写死在 `_pages/about.md`。
- 当前没有公开简历下载 PDF 路径；`_config.yml` 中 `cv_pdf` 为空。
- 当前没有明确的 Google Scholar、GitHub、LinkedIn、ORCID 配置值；这些字段在 `_config.yml` 中存在但为空。
