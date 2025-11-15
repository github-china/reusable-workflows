<header>

<!--
  <<< Author notes: Course header >>>
  Read <https://skills.github.com/quickstart> for more information about how to build courses using this template.
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses MIT license.
-->

[English](https://github.com/skills/reusable-workflows) | 中文

> 本课程翻译自 Github Skills，全部课程请点击 [这里查看](https://www.github-zh.com/getting-started)

# 可复用的工作流 & 矩阵策略

_本课程中，我们将创建一个可复用的工作流，在另一个工作流中调用它，并使用[矩阵策略](https://docs.github.com/zh/actions/how-tos/write-workflows/choose-what-workflows-do/run-job-variations) 同时运行多个版本。_

</header>

<!--
  <<< Author notes: Course start >>>
  Include start button, a note about Actions minutes,
  and tell the learner why they should take the course.
-->

## Welcome

创建可复用的工作流，可降低人工维护成本，避免在多个仓库中回来复制代码。
而结合[矩阵策略](https://docs.github.com/zh/actions/how-tos/write-workflows/choose-what-workflows-do/run-job-variations)， 则可以在单个作业定义中使用变量，自动组合出多个运行版本。

- **目标人群**: 开发者、运维、学生、管理者、团队成员、GitHub 用户。
- **你将学到**: 如何编写和使用可复用工作流、如何创建矩阵策略、如何触发工作流，如何查看Actions日志。
- **你将完成**: 一个带有矩阵策略的 Actions 工作流，它会调用一个可复用工作流，并输出多个 Node.js 版本。
- **先决条件**: 本课程会用到 Pull Request 和 YAML workflow 文件。建议你先学习 [GitHub 入门课程](https://github.com/github-china/introduction-to-github)，或已经熟悉 GitHub 基本操作；同时也建议看过 [Hello GitHub Actions](https://github.com/github-china/hello-github-actions)，以了解 Actions 的基本概念。
- **课程时长**: 不到一小时。
- **致谢**: 本课程灵感来自[@mickeygousset](https://github.com/mickeygousset)的一段[演示视频](https://www.youtube.com/watch?v=MBpyouQtY_M)。

在本课程中，你将完成以下步骤：

1. 创建一个可复用的工作流（workflow）
2. 添加一个新作业（job）
3. 添加矩阵策略（matrix strategy）
4. 合并你的 Pull Request
5. 触发 workflow

### 如何开始课程

<!-- For start course, run in JavaScript:
'https://github.com/new?' + new URLSearchParams({
  template_owner: 'skills',
  template_name: 'reusable-workflows',
  owner: '@me',
  name: 'skills-reusable-workflows',
  description: 'My clone repository',
  visibility: 'public',
}).toString()
-->

[![start-course](https://user-images.githubusercontent.com/1221423/235727646-4a590299-ffe5-480d-8cd5-8194ea184546.svg)](https://github.com/new?template_owner=github-china&template_name=reusable-workflows&owner=%40me&name=skills-reusable-workflows&description=My+clone+repository&visibility=public)

1. 右键点击上方 **Start course** 按钮，选择在新标签页中打开链接。
2. 在新页面中根据系统提示新建一个仓库。
   - 仓库名称、描述这些字段系统已经帮我们自动填充好了，您可以按需修改。
   - 建议选择公开仓库，因为私有仓库有[GitHub Actions 分钟数限制](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions)。
   - 最后点击 Create repository 按钮
3. 仓库创建完毕后，等待大约 20 秒（等待Action执行），然后刷新页面。注意是刷新您仓库的页面，不是本课程的页面。如果页面没有变化，请继续等待。然后按照 README 中的步骤一步步进行。

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/reusable-workflows) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
