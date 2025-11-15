<!--
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 3: 为工作流添加矩阵策略（matrix strategy）

_干得漂亮! :sparkles:_

你的 My Starter Workflow 现在已能调用 Reusable Workflow。
它会在 Actions 日志中打印类似 “The node version to use is: 14” 的消息。虽然我们还没实际查看日志，但别急，下一步就会看到。

现在，我们来进一步优化这个工作流：不再只运行一个固定的版本，而是通过矩阵策略（matrix strategy）同时测试多个 Node.js 版本。

**什么是矩阵策略**: 矩阵策略允许你在一个 job 中定义多个变量，GitHub Actions 会根据变量的所有组合自动生成多个 job 运行。
比如你想让代码在不同 node 版本、不同操作系统下都跑一遍，就可以用 matrix 实现，而不用手写多个 job。

例如下面：
```yaml
jobs:
  example_matrix:
    strategy:
      matrix:
        version: [10, 12, 14]
        os: [ubuntu-latest, windows-latest]
```

要使用矩阵策略，先在 job 中添加 `strategy` 关键字，再嵌套一个 `matrix` 块。这里我们定义了两个变量：

* `version`: 10、12、14
* `os`: ubuntu-latest、windows-latest

Actions 会将它们进行组合运行，因此总共会执行 **6 个 job**（3×2）。
相较于重复写 6 个 job，矩阵策略显然更优雅、更易维护。

现在，让我们也给 **My Starter Workflow** 加上矩阵策略，让它用不同的 node 版本执行同一个 job，而不是固定写死 `14`。

### :keyboard: 实操环节：使用矩阵策略同时运行多个 node 版本

1. 打开 `my-starter-workflow.yml` 文件。
2. 在 `call-reusable-workflow` 这个 job 下添加 `strategy`。
3. 在 `strategy` 下添加 `matrix`。
4. 定义一个名为 `nodeversion` 的变量，让它依次运行以下 node 版本：
   `[14, 16, 18, 20]`
5. 将原本写死的 node 值 `14` 替换为矩阵中的值，使用语法：
   `${{ matrix.nodeversion }}`
   修改后的 job 示例：

   ```yaml
   call-reusable-workflow:
     strategy:
       matrix:
         nodeversion: [14, 16, 18, 20]
     uses: ./.github/workflows/reusable-workflow.yml
     with:
       node: ${{ matrix.nodeversion }}
   ```

6. 点击 **Start commit** → **Commit changes** 提交修改。
7. 等待大约 20 秒后刷新当前教程页面，该步骤会自动完成并进入下一步。