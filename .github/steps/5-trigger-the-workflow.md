<!--
  <<< Author notes: Step 5 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 5: 触发你的 workflow 并查看 Actions 日志

_你已经接近尾声了，这是最后一步！! :heart:_

现在你已经把所有改动合并进 `main` 分支，我们来手动触发 **My Starter Workflow**，看看一切是否按预期运行。在开始之前，先回顾一下我们预期会看到什么：

* 我们应该看到 **My Starter Workflow** 启动 **五个 job**。还记得是什么吗？
  一个是 `build` job，另一个是 `call-reusable-workflow`，它会基于 matrix 运行多个版本的 node。
  ![Screen Shot 2022-09-08 at 9 53 52 AM](https://user-images.githubusercontent.com/6351798/189220189-97361a5e-eecf-4666-a859-e0587354bafe.png)

* 我们还应该看到可复用 workflow 在不同 node 版本下打印的 echo 消息（即 matrix 的每个版本都会打印 node 版本）。
  ![Screen Shot 2022-09-08 at 9 52 41 AM](https://user-images.githubusercontent.com/6351798/189220620-0576540a-366f-44e1-866c-2955af399cdb.png)

### :keyboard: 实操环节

1. 打开你仓库的 **Actions** tab页。
2. 在左侧选择 **My Starter Workflow**，然后点击 **Run workflow** 按钮，选择 **Main** 分支并运行。
3. 等几秒钟，等待新的 workflow run 出现在队列中。出现后，点击这个 **My Starter Workflow** 运行记录。

左侧你会看到所有构建 job 的列表：一个 `build`，以及基于 matrix 的 4 个 node 版本（14、16、18、20）。
当其中某个版本的 job 执行完成后，你可以点进去查看 **Output the input value** 步骤，它会打印来自可复用 workflow 的输出内容。

当你查看完 Actions 日志后，回来刷新此页面即可完成课程！🎉