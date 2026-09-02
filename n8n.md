啊，你说的是 n8n utils 这个 VS Code Extension。这个和我刚才说的 n8n as code 完全不是一个定位。

n8n utils - VS Code Marketplace⁠￼
n8n-utils GitHub⁠￼

它主要是给开发 n8n 本身 / 开发 n8n Node的人用的工具集，而不是用来画普通 workflow 的。

它主要有这些能力：

功能	干什么
Launch n8n	VS Code 里直接启动 n8n
Hot Reload	修改 Node 代码后自动重载
Node Params	浏览 Node 的参数树并跳转源码
Controller Navigator	浏览 n8n 后端 controller / endpoint
Env Vars Tooltip	鼠标放到环境变量上直接看值和状态
Stored Workflows	查看本地 SQLite 中保存的 workflow
Node Stats	看 Node 使用统计，但这是 n8n 团队内部功能

例如你在开发一个自己的 Node：

VS Code
│
├─ MyNode.node.ts
│     ↑
│   修改代码
│
├─ n8n utils
│     ↓ hot reload
│
└─ n8n
      ↓
   localhost:5678
      ↓
浏览器测试 MyNode

最有用的是 Command Palette 里的：

Ctrl + Shift + P
n8n-utils: Launch n8n in VSCode
n8n-utils: Navigate to node parameter
n8n-utils: Navigate to controller endpoint

尤其是 Node parameter navigator。如果一个 Node 有几十个配置参数，你可以在侧边栏看到参数树，然后直接跳到对应的 *.node.ts / *Description.ts。Controller navigator 则更偏向你在研究 n8n 源码本身的时候用。

不过有个很重要的问题：这个扩展很老了。Marketplace 当前显示的版本是 1.1.2，最后更新在 2023 年 5 月；2025 年 n8n 社区里也已经有人反馈它似乎处于 abandoned 状态、Launch 功能在其环境里不可用。

所以如果你的目的只是：

我自己用 n8n
↓
做 Workflow
↓
Code Node
↓
HTTP / SSH / Redmine / Keycloak

基本不需要 n8n utils。

它真正适合的是：

我要开发 n8n 源码
        或
我要开发 Custom / Community Node
        ↓
      VS Code
        ↓
    n8n utils

另外别把它和官方 npm 包 @n8n/utils 搞混。后者是 n8n 当前仍在维护的 TypeScript utility package，用于 n8n 前后端代码共享工具函数，并不是 VS Code Extension。

如果你现在的目标是“我想用 VS Code 正规开发自己的 n8n workflow，而不是开发 n8n 源码”，那我可以继续给你筛一下 2026 年现在还在维护、真正适合 Workflow 开发的 VS Code 扩展。



对，你说的是 n8n Utils 里的 “Focus on Controller Endpoints View”。这个功能不是拿来开发 workflow 的，而是给你阅读 / 开发 n8n 本体后端源码用的。

它的作用是把 n8n 后端的 *.controller.ts 里的 API endpoint 集中显示出来。官方 README 把它叫 Controller endpoint navigator，并明确说明只支持 *.controller.ts。

例如 n8n 源码里可能有类似：

@RestController('/credentials')
export class CredentialsController {
  @Get('/')
  getCredentials() {}
  @Post('/')
  createCredential() {}
  @Delete('/:id')
  deleteCredential() {}
}

你不用自己到处搜 controller，而是在 VS Code 里执行：

Ctrl + Shift + P
↓
n8n-utils: Navigate to controller endpoint

或者你看到的：

n8n-utils: Focus on Controller Endpoints View

它会把焦点切到侧边栏里的 n8n controllers View，然后你可以按：

Controller
├─ CredentialsController
│  ├─ GET    /credentials
│  ├─ POST   /credentials
│  └─ DELETE /credentials/:id
│
├─ WorkflowController
│  ├─ GET    /workflows
│  ├─ POST   /workflows
│  └─ ...

点击其中一个 endpoint，就会直接跳到对应的 TypeScript controller 源码。

关键是你必须打开 n8n 源码仓库。 比如：

git clone https://github.com/n8n-io/n8n.git
cd n8n
code .

然后 n8n Utils 才能扫描 n8n 的 *.controller.ts。如果你打开的只是你自己的 workflow 项目：

my-n8n-workflows/
├── workflow1.json
├── workflow2.json
└── ...

这个 View 基本没东西可看。

所以这也印证了我们前面说的：

n8n Utils 主要是给“开发 n8n 本体”的人用的，不是给“用 n8n 开发 workflow”的人用的。

如果你的目标是 读 n8n 源码、研究 n8n REST API 后端是怎么实现的，这个 Controller Endpoints View 反而非常方便；如果目标是 VS Code + AI Agent 开发 workflow，还是前面那个 n8n as code 更对路。

n8n Utils GitHub⁠￼

