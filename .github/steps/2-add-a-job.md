<!--
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 2: 添加一个 Job 来调用可复用工作流

_:tada: 你已经成功让一个 workflow 变得可复用了!_

现在，你已经有了一个可复用工作流，接下来就可以在其他 workflow 中调用它。不过，在动手之前，先花一分钟了解一下这个可复用工作流具体做了什么。

```yaml
name: Reusable Workflow

on:
  workflow_call:
    inputs:
      node:
        required: true
        type: string

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Output the input value
        run: |
          echo "The node version to use is: ${{ inputs.node }}"
```

它要求调用方必须传入一个名为 `node` 的输入参数（input），否则无法运行。随后它会启动名为 `build` 的 job，并在 `ubuntu-latest` 环境上执行

`build` job 里有两个步骤：

1. 使用 `actions/checkout@v4` 检出代码；
2. 接着通过 echo 命令在 Actions 日志中打印出传入的 Node.js 版本，例如：`The node version to use is: 14`。

了解完这个可复用 workflow 的逻辑后，接下来我们要在另一个 workflow（**my-starter-workflow**）里新增一个 job，通过 `uses:` 引用我们刚才的可复用工作流。同时记得传入 `node` 参数，否则复用流程不会执行。

### :keyboard: 实操环节

1. 打开 `.github/workflows/` 目录，找到并打开 `my-starter-workflow.yml`。
2. 在 workflow 中新增一个名为 `call-reusable-workflow` 的 job。
3. 使用 `uses` 指定我们要调用的 workflow 文件路径（即 `reusable-workflow.yml`）。
4. 用 `with` 传入参数 `node`，并将它的值设为 `14`：

   ```yaml
   call-reusable-workflow:
     uses: ./.github/workflows/reusable-workflow.yml
     with:
       node: 14
   ```

5. 点击 **Start commit**，然后点击 **Commit changes** 提交修改。
6. 等待约 20 秒后刷新本页面。GitHub Actions 会自动检测到你的更改，并进入下一步。