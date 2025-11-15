<!--
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
-->

## Step 1: 让 workflow 变的可复用

_欢迎来到 "Reusable Workflows and Matrix Strategies" 课程! :wave:_

GitHub Actions 的使用范围非常广：你可以用它来自动化重复性任务、搭建 CI/CD 流水线，几乎涵盖软件开发流程中的任何环节。

无论你是刚接触 GitHub Actions，还是已经经验丰富，你都会很快发现：同样的任务和步骤总是在不同 workflow 里重复出现，甚至需要在不同仓库之间不断复制粘贴，既麻烦又不利于维护。

有没有办法减少这些重复工作呢？当然有！这就是我们今天学习的主题：**可复用的工作流（reusable workflows）**。

**使用可复用工作流有什么好处？**
顾名思义，可以被重复使用。通过将流程抽成可复用的 workflow，不用在多个仓库中重复维护相同的 workflow 文件。

* 举个例子：如果你有三个 Node 项目，它们的构建方式完全一样，那么只需要准备一个可复用 workflow，就不用在三个仓库里来回复制。

**那我已有的 workflow，要怎么改造成可复用工作流？**
可复用工作流本质上与普通的 GitHub Actions workflow 一样，唯一的区别是它必须包含一个特殊的触发器：`workflow_call`。
它的作用与 `push`、`issues`、`workflow_dispatch` 类似，但用途是让别的 workflow 可以「调用」它。

因此，要让一个 workflow 可复用，只需要把触发器改成 `workflow_call` 即可。

下面我们就动手体验一下。

### :keyboard: 实操环节: 为工作流添加 `workflow_call` 触发器

1. 打开一个新的浏览器标签页，方便一边操作一边阅读教程。
2. 进入仓库的 **Code** 页。
3. 切换到 **reusable-workflow** 分支。
4. 打开 `.github/workflows/` 目录，然后点击 **reusable-workflow.yml**。
5. 将其中的 `workflow_dispatch` 触发器替换为 `workflow_call`。修改后应如下所示：

   ```yaml
   name: Reusable Workflow

   on:
     workflow_call:
       inputs:
         node:
           required: true
           type: string
   ```

6. 点击 **Start commit**，然后点击 **Commit changes** 提交修改。
7. （可选）你可以创建一个 Pull Request，方便查看这门课程中所有的修改记录。进入 **Pull Requests** → **New pull request**，选择 `base: main`、`compare: reusable-workflow`。
8. 等待约 20 秒后刷新本页面。[GitHub Actions](https://docs.github.com/en/actions) 会自动检测到你的更改，并进入下一步。