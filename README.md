# macOS / Linux（bash/zsh）一条龙


curl -LsSf https://astral.sh/uv/install.sh
 | sh &&
export DASHSCOPE_API_KEY="<你的DashScopeKey>" &&
mkdir -p md &&
uv run python main.py --index ./md &&
uv run python main.py

# Windows（PowerShell）


powershell -c "irm https://astral.sh/uv/install.ps1
 | iex" ; $env:DASHSCOPE_API_KEY="<你的DashScopeKey>" ;
mkdir md -Force | Out-Null ; uv run python main.py --index ./md ;
uv run python main.py