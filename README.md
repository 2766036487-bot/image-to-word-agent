# GLM-4.5-Flash 图片转Word智能体（学生版）
基于智谱GLM-4.5-Flash大模型驱动的图片转Word智能体，全程免费，适配学生学习/日常使用场景。

## ✨ 核心功能
- 🧠 大模型自主判断用户意图，自动调用OCR工具处理图片
- 📝 识别图片中的文字/表格，生成**宋体**格式的Word文档
- 🌐 本地FastAPI可视化接口，无需写代码，浏览器直接操作
- 🆓 全程免费（GLM-4.5-Flash无付费项，EasyOCR开源免费）

## 📋 环境准备（学生零基础友好）
### 1. 创建Python虚拟环境（推荐Anaconda）
```bash
# 创建虚拟环境（Python3.9兼容性最佳）
conda create -n ocr_word_env python=3.9
# 激活虚拟环境
conda activate ocr_word_env
2. 安装依赖包
bash
运行
# 一键安装所有依赖（清华源提速）
pip install fastapi uvicorn python-multipart easyocr python-docx openai python-dotenv -i https://pypi.tuna.tsinghua.edu.cn/simple
⚙️ 配置步骤（关键！）
1. 获取智谱 API Key
注册智谱 AI 开放平台：https://open.bigmodel.cn/
完成实名认证（学生免费，仅需身份证）
进入「控制台→API 密钥」生成并复制你的 API Key
2. 创建环境配置文件
在项目根目录新建.env文件，填入以下内容（替换为自己的路径 / API Key）：
env
# 智谱GLM-4.5-Flash API Key
GLM_API_KEY="你的智谱API Key"
# EasyOCR模型存储路径
EASYOCR_MODEL_PATH="D:\EasyOCR_Models"
# 图片上传目录
UPLOAD_DIR="D:\pythonProject\pythonProject\ImageToWordGitHub\uploads"（自己的路径即可）
# Word输出目录
OUTPUT_DIR="D:\pythonProject\pythonProject\ImageToWordGitHub\outputs"
🚀 启动智能体
bash
运行
# 运行核心代码
python llm_ocr_agent.py
启动成功后，浏览器访问：http://127.0.0.1:8000/docs
📖 使用教程（傻瓜式操作）
在http://127.0.0.1:8000/docs页面找到/agent/process/接口，点击「Try it out」
user_query：输入指令（如把这张图片转成Word文档）
file：点击「Choose File」选择要处理的图片（支持 jpg/png）
点击「Execute」，等待 3-10 秒
复制返回结果中的download_url，在浏览器打开即可下载 Word 文档
📁 项目结构
plaintext
ImageToWordGitHub/
├── llm_ocr_agent.py    # 智能体核心代码
├── .env                # 敏感配置（不上传GitHub）
├── .gitignore          # Git过滤规则
├── requirements.txt    # 依赖清单
└── README.md           # 使用说明
🎓 学生使用注意事项
.env文件包含敏感 API Key，切勿上传到 GitHub（已通过.gitignore 过滤）
EasyOCR 首次运行会自动下载模型（约几百 MB），耐心等待即可
仅支持 jpg/png 格式图片，建议图片大小不超过 5MB
该项目仅用于学习交流，请勿商用
❓ 常见问题
Q1：启动时报Using CPU？
A1：正常现象！无 GPU 也能运行，仅识别速度稍慢，不影响功能。
Q2：访问http://127.0.0.1:8000报 404？
A2：需访问http://127.0.0.1:8000/docs（带 /docs 后缀），这是 FastAPI 的可视化接口地址。
Q3：生成的 Word 乱码？
A3：代码已默认设置宋体，若乱码请检查 Word 的字体显示设置。
