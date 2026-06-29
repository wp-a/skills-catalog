# WPIRONMAN Skills Catalog

这是 [WPIRONMAN Skills](https://www.wpironman.top/skills/) 的公开数据源仓库。

页面 UI 仍然在博客仓库里维护，skill 内容、分类、任务入口、执行栈和实战手册都在这个仓库维护。这样后续新增 skill 不需要改页面代码，只需要改 JSON，再同步到博客。

## 目录结构

```text
skills/*.json                 每个 skill 一个文件
manifest.json                 声明要发布哪些 skill 文件
marketplace-categories.json   目录分类
collections.json              首页/精选集合
task-briefs.json              “先选任务”入口
stack-blueprints.json         可执行 skill 组合
discovery-routes.json         按工作流浏览的路径
reference-patterns.json       目录质量标准
runbooks.json                 高风险实战手册
defaults-by-category.json     分类默认详情字段
skill.schema.json             skill 字段约束参考
```

## 新增一个 Skill

1. 在 `skills/` 下新增一个文件，例如 `skills/example-skill.json`。
2. 把这个文件路径加入 `manifest.json` 的 `files.skills`。
3. 在 `marketplace-categories.json` 里把 skill id 放进一个具体分类。
4. 按需要加入 `collections.json`、`task-briefs.json`、`stack-blueprints.json` 或 `discovery-routes.json`。
5. 回到博客仓库同步并验证：

```bash
cd /Users/wangpeng/博客/Hexo_Blog_Source
npm run sync:skills-catalog
npm test
npx hexo generate --force
```

如果只是本地预览 catalog 改动，还没推到 GitHub，可以这样同步：

```bash
cd /Users/wangpeng/博客/Hexo_Blog_Source
SKILLS_CATALOG_BASE=/Users/wangpeng/博客/skills-catalog npm run sync:skills-catalog
```

## 必填字段

每个 `skills/*.json` 至少需要这些字段：

- `id`
- `name`
- `source`
- `origin`
- `category`
- `creator`
- `workflow`
- `installType`
- `status`
- `quality`
- `description`
- `bestFor`
- `avoidWhen`
- `verification`
- `install`
- `repo`
- `tags`

博客同步脚本会用 `defaults-by-category.json` 补齐 `userRole`、`input`、`output`、`failureModes`、`quickStart`、`trust` 等详情字段。

## 策展规则

不要为了数量堆链接。一个 skill 只有同时满足下面条件，才适合加入公开目录：

- 有明确的公开仓库或可追溯来源。
- 有清楚的使用场景，不是泛泛的提示词合集。
- 有适用边界和不适用场景。
- 有至少两条可以复查的验证标准。
- 安装命令或使用入口可以被别人复制执行。

## 当前维护入口

- 公开仓库：[wp-a/skills-catalog](https://github.com/wp-a/skills-catalog)
- 网站页面：[WPIRONMAN Skills](https://www.wpironman.top/skills/)
- 提交建议：[Issues](https://github.com/wp-a/skills-catalog/issues)
