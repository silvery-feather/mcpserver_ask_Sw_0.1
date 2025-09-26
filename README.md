# macOS / Linux（终端 / VSCode 终端）

##  选择一个提前准备好的空文件夹
cd ---

## 0) 安装 uv（包管理 + Python 管理）
curl -LsSf https://astral.sh/uv/install.sh | sh

## 1) 安装一个可用的 Python 版本（与你的依赖最稳的版本）
uv python install 3.12

## 2) 克隆仓库 // 直接下载可以忽略
git clone https://github.com/silvery-feather/mcpserver_ask_Sw_0.1  
cd mcpserver_ask_Sw_0.1

## 3) 设置 DashScope Key（仅本次终端会话）
```bash
export DASHSCOPE_API_KEY=替换为你的Key
```
## 4) 启动 MCP（stdio）
### --python 3.12：强制用上面装好的 3.12 运行时
### 首次运行会按 pyproject.toml 自动安装依赖（faiss/numpy 等）
uv run --python 3.12 python main.py
（运行完在终端ctrl c终止即可，本mcpserver默认为stdio,所以不需要一直启动）



# Windows（PowerShell）

## 0) 安装 uv
iwr https://astral.sh/uv/install.ps1 -UseBasicParsing | iex

## 1) 安装 Python 3.12（由 uv 管理，无需单独装 Python）
uv python install 3.12

## 2) 克隆仓库
git clone https://github.com/silvery-feather/mcpserver_ask_Sw_0.1
cd mcpserver_ask_Sw_0.1

## 3) 设置 DashScope Key（仅当前窗口）
$env:DASHSCOPE_API_KEY="替换为你的Key"

## 4) 启动 MCP（stdio），依赖会自动按 pyproject 安装
uv run --python 3.12 python main.py



# 一些其他部分
## 如果你想要将该配置配置到cursor中

1.打开cursor的 cursor setting

2.在左侧列表找到mcp

3.点击add new custom mcp server

4.此时你会发现打开了一个叫做mcp.json的文件，直接复制粘贴即可
### Cherry / MCP 配置示例（JSON）

```json
{
  "mcpServers": {
    "swanlab-docs": {
      "command": "uv",
      "args": [
        "run",
        "--with", "mcp",
        "--with", "openai",
        "--with", "faiss-cpu",
        "--with", "numpy",
        "--with", "regex",
        "--with", "tqdm",
        "python",
        "你的前置文件路径/mcpserver_ask_Sw_0.1/main.py",
        "--auto"
      ],
      "env": {
        "DASHSCOPE_API_KEY": "YOUR_DASHSCOPE_KEY_HERE",
        "INDEX_DIR": "你的前置文件路径/mcpserver_ask_Sw_0.1/rag_cache/api_v1",
        "DEFAULT_DOCS_ROOT": "你的前置文件路径/mcpserver_ask_Sw_0.1/md"
      }
    }
  }
}
```
(注意！：如果你是直接下载的zip格式那么你的一级文件夹名可能会叫做“mcpserver_ask_Sw_0.1-main”,请注意识别)
5.回到setting界面，看到添加的mcp显示绿色小点以及1 tool ennale 即可，注意，只能在agent模式下进行。












