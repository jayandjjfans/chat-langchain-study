# chat-langchain-study

❗❗❗从0开始运行这个项目，语雀版本（和本文内容一模一样，看一个就行）❗❗❗：[chat-langchain项目启动攻略](https://www.yuque.com/goodnote/llm-dev/zwwg6hu8b5chwl1u)


本文详细介绍如何运行一个入门级项目，即 langchain 官方项目 chat-langchain 项目启动和运行时候的一些细节。欢迎阅读，如果对你有用，麻烦点一下 🌟 star，谢谢！



资源如下：

> 1. 源仓库地址：[https://github.com/langchain-ai/chat-langchain](https://github.com/langchain-ai/chat-langchain)
> 2. 可本地运行分支（有版本兼容性问题，需要更改，可直接使用本人调试过的代码，也可根据视频中一步一步的解决）：[https://github.com/langchain-ai/chat-langchain/tree/langserve](https://github.com/langchain-ai/chat-langchain/tree/langserve)
> 3. 🔥 本人已经更改**调试能运行**的仓库代码🔥(**本项目**)：[https://github.com/lichuachua/chat-langchain-study](https://github.com/lichuachua/chat-langchain-study)
>

本文一共三部分：

1. 第一部分是项目的运行效果，直接运行上面 “[3. 🔥 本人已经更改**调试能运行**的仓库代码🔥](https://github.com/lichuachua/chat-langchain-study)”即可得到运行效果。建议先看一遍，知道这个项目实现起来是什么样子。
2. 第二部分是申请项目启动需要的API，主要是项目启动需要的环境变量。不涉及代码，只是申请运行项目需要的Key。
3. 第三部分是如何从源仓库地址拉取项目源码进行更改（当然，这部分可以直接看我改过的代码“[3. 🔥 本人已经更改**调试能运行**的仓库代码🔥](https://github.com/lichuachua/chat-langchain-study)”），之后导入第二部分得到的API，开始运行，运行起来的项目效果同第一部分。

# 运行效果
直接运行“[3. 🔥 本人已经更改**调试能运行**的仓库代码🔥](https://github.com/lichuachua/chat-langchain-study)”，运行效果如视频所示：

**<font style="color:#D22D8D;">视频：</font>**

> 录制：01-运行效果.mov
>
> 日期：2025-06-23 09:53:42
>
> 录制文件：[https://meeting.tencent.com/crm/NoqewwVa21](https://meeting.tencent.com/crm/NoqewwVa21)
>

# 准备工作（申请API）
API平台（先注册，再申请）：

1. supabase：[https://supabase.com](https://supabase.com)
2. weaviate：[https://console.weaviate.cloud/](https://console.weaviate.cloud/)
3. LangSmith：[https://smith.langchain.com/](https://smith.langchain.com/)
4. Open API：[https://platform.openai.com/](https://platform.openai.com/)

> 注意：Open API需要**先充值**再使用。
>

申请API的详细步骤如下：

**<font style="color:#D22D8D;">视频：</font>**

> 录制：02-申请API.mov
>
> 日期：2025-06-23 09:53:42
>
> 录制文件：[https://meeting.tencent.com/crm/NgYd99zgc8](https://meeting.tencent.com/crm/NgYd99zgc8)
>

# chat-langchain_项目运行成功
**<font style="color:#D22D8D;">视频：</font>**

> 录制：03-兼容项目启动.mov
>
> 日期：2025-06-23 09:53:42
>
> 录制文件：[https://meeting.tencent.com/crm/2rE5PyzXa1](https://meeting.tencent.com/crm/2rE5PyzXa1)
>

## 直接运行更改后的代码
直接运行我已经更改后的代码，**不需要任何的代码变更**，

上述“项目运行成功视频”中<font style="color:#DF2A3F;">第一步的项目拉取换成拉取更改后的代码就好</font>，<font style="color:#DF2A3F;">视频</font>中**<font style="color:#DF2A3F;">涉及到代码的变更完全不需要改</font>**跟着**<font style="color:#DF2A3F;">看运行流程</font>**就好，具体执行如下：

### 克隆代码
克隆“[3. 🔥 本人已经更改**调试能运行**的仓库代码🔥](https://github.com/lichuachua/chat-langchain-study)”执行：

```plain
git clone https://github.com/lichuachua/chat-langchain-study
```

### <font style="color:rgb(31, 35, 40);">安装后端依赖</font>
执行：<font style="color:rgb(31, 35, 40);background-color:rgba(129, 139, 152, 0.12);">poetry install</font>

### 需要导入的环境变量
下面的环境变量改为第二步“准备工作（申请API）”得到的API

```plain
export OPENAI_API_KEY=""
export WEAVIATE_URL=""
export WEAVIATE_API_KEY=""
export RECORD_MANAGER_DB_URL=""
# for tracing
export LANGCHAIN_TRACING_V2=true
export LANGCHAIN_ENDPOINT="https://api.smith.langchain.com"
export LANGCHAIN_API_KEY=""
export LANGCHAIN_PROJECT=""
```

### WEAVIATE数据库版本
查看版本：pip show weaviate-client，如果是**3.26.2版本**，则会版本不匹配，需要降低版本：

1. 先卸载当前的 Weaviate：

```bash
pip uninstall weaviate-client -y
```

2. 安装 Weaviate v3.x（例如 3.25.3 是稳定版本）

```bash
pip install weaviate-client==3.25.3
```



> ⚠️ `3.25.3` 是 2024 年初的稳定版本，兼容 LangChain 的所有 vectorstore 代码。
>

### 运行代码

这部分参考源仓库的可本地运行分支版本的内容就好了，不需要改任何代码，我已经改过了：
1. 运行 `python backend/ingest.py` 执行 文档数据提取到 Weaviate vectorstore 中（只需完成一次）。
2. 使用 `make start` 启动 Python 后端，后端运行在 8080 端口。
3. 通过运行 `cd ./frontend` 进入到前端目录，然后安装前端依赖项，运行：`yarn`。
4. 使用 `yarn dev` 运行前端，前端运行在 3000 端口。

## 运行并且更改官方仓库
> 如果你不想运行我改后的代码，而是🔥运行并且更改官方仓库🔥：

这部分是下载官方仓库代码，**需要修改源代码**才能使用，完全按照视频中的内容，一字不差的改就好。

### 克隆并且切换代码
源仓库地址：

git clone [https://github.com/langchain-ai/chat-langchain](https://github.com/langchain-ai/chat-langchain)

git fetch origin langserve:langserve

git checkout langserve

git branch

### <font style="color:rgb(31, 35, 40);">安装后端依赖</font>
执行：<font style="color:rgb(31, 35, 40);background-color:rgba(129, 139, 152, 0.12);">poetry install</font>

### 修改代码并且拉取依赖
可能会用到下面的命令：

拉取依赖：pip install -U langchain-community

### 修改代码中向量化的数据资源量
修改ingest.py中的向量化文件数量，不修改会花费较多的API。

### 需要导入的环境变量
下面的环境变量改为第二步“准备工作（申请API）”得到的API

```plain
export OPENAI_API_KEY=""
export WEAVIATE_URL=""
export WEAVIATE_API_KEY=""
export RECORD_MANAGER_DB_URL=""
# for tracing
export LANGCHAIN_TRACING_V2=true
export LANGCHAIN_ENDPOINT="https://api.smith.langchain.com"
export LANGCHAIN_API_KEY=""
export LANGCHAIN_PROJECT=""
```

### WEAVIATE数据库版本
查看版本：pip show weaviate-client，如果是3.26.2，则说明没有版本太新了：

1. 先卸载当前的 Weaviate：

```bash
pip uninstall weaviate-client -y
```

2. 安装 Weaviate v3.x（例如 3.25.3 是稳定版本）

```bash
pip install weaviate-client==3.25.3
```



> ⚠️ `3.25.3` 是 2024 年初的稳定版本，兼容 LangChain 的所有 vectorstore 代码。
>



### 运行后端代码
1. 运行 `python backend/ingest.py` 执行 文档数据提取到 Weaviate vectorstore 中（只需完成一次）。
2. 使用 `make start` 启动 Python 后端，后端运行在 8080 端口。

<font style="color:rgb(31, 35, 40);"></font>

### <font style="color:rgb(31, 35, 40);">修改前端代码</font>
修改：chat-langchain/frontend/app/components/ChatMessageBubble.tsx文件 中第 5 81 108 行：
1. 删除原代码的第5行：`import * as DOMPurify from "dompurify"`;
2. 更改原代码的第81行`__html: DOMPurify.sanitize(content.slice(prevIndex, match.index))`,改为：`__html: content.slice(prevIndex, match.index),`
3. 更改原代码的第108行`__html: DOMPurify.sanitize(content.slice(prevIndex)),` 改为：`__html: content.slice(prevIndex),`

### 运行前端代码
1. 通过运行 `cd ./frontend` 进入到前端目录，然后安装前端依赖项，运行：`yarn`。
2. 使用 `yarn dev` 运行前端，前端运行在 3000 端口。






1.export PATH="/Users/hetongxue/.local/bin:$PATH"   否则potry命令不存在，无法进行make start
2.导入一系列环境变量
export OPENAI_API_KEY=""
export WEAVIATE_URL=""
export WEAVIATE_API_KEY=""
export RECORD_MANAGER_DB_URL=""
export LANGCHAIN_TRACING_V2=true
export LANGCHAIN_ENDPOINT="https://api.smith.langchain.com"
export LANGCHAIN_API_KEY=""
export LANGCHAIN_PROJECT=""
3.conda activate base  否则一开始poetry install 的工具包可能不存在？
4.poetry install 只执行一次
5.python backend/ingest.py 只执行一次
6.make start 启动后端
(另开一个终端)
7.`cd ./frontend` 进入到前端目录，然后安装前端依赖项，运行：`yarn`。
8.使用 `yarn dev` 运行前端，前端运行在 3000 端口。
