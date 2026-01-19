# GLM-4.5-Flash 图片转Word智能体（学生版）
基于智谱GLM-4.5-Flash大模型驱动的免费图片转Word工具，适配学生学习/日常办公场景，无需复杂操作，浏览器即可使用。

## 核心功能
- 🧠 大模型自主识别需求，自动调度OCR工具
- 📝 精准提取图片文字/表格，生成宋体Word文档
- 🌐 本地可视化接口，无需编写代码
- 🆓 全程免费（GLM-4.5-Flash+EasyOCR双开源）
- 📊 自动去重、排版规整，保留原图内容顺序

## 环境准备
### 1. 搭建Python虚拟环境（推荐Anaconda）
```bash
# 创建虚拟环境（Python 3.9兼容性最佳）
conda create -n ocr_word_env python=3.9
# 激活虚拟环境
conda activate ocr_word_env
### 2. 安装依赖包（一键执行）
bash
运行
pip install fastapi uvicorn python-multipart easyocr python-docx openai python-dotenv -i https://pypi.tuna.tsinghua.edu.cn/simple
### 配置步骤
1. 获取智谱 API Key
注册智谱 AI 开放平台：https://open.bigmodel.cn/
完成实名认证（学生免费，仅需身份证）
进入「控制台 → API 密钥」，生成并复制个人 API Key
2. 创建环境配置文件
在项目根目录新建 .env 文件，粘贴以下内容并修改为自己的信息：
env
# 智谱GLM-4.5-Flash API Key（替换为你的密钥）
GLM_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
# EasyOCR模型存储路径（默认即可）
EASYOCR_MODEL_PATH="D:\EasyOCR_Models"
# 图片上传临时目录（自动创建）
UPLOAD_DIR="D:\pythonProject\pythonProject\ImageToWordGitHub\uploads"
# Word输出目录（自动创建）
OUTPUT_DIR="D:\pythonProject\pythonProject\ImageToWordGitHub\outputs"
### 启动与使用
1. 启动智能体服务
bash
运行
# 运行核心代码
python llm_ocr_agent.py
启动成功提示：Uvicorn running on http://0.0.0.0:8000
2. 浏览器操作流程
打开可视化接口：http://127.0.0.1:8000/docs
找到 /agent/process/ 接口，点击「Try it out」
输入指令（如：把这张图片转成Word文档）
点击「Choose File」，上传需要处理的图片（支持 jpg/png）
点击「Execute」，等待 3-10 秒（首次识别稍慢）
复制返回结果中的 download_url，打开即可下载 Word 文档
### 项目结构
plaintext
ImageToWordGitHub/
├── llm_ocr_agent.py    # 智能体核心代码（大模型+OCR+接口）
├── .env                # 敏感配置文件（API Key+路径，不上传GitHub）
├── .gitignore          # Git过滤规则（避免上传无用/敏感文件）
├── requirements.txt    # 依赖清单（一键安装）
└── README.md           # 完整使用说明
### 注意事项
.env 文件包含 API Key，切勿上传到 GitHub（已通过 .gitignore 自动过滤）
EasyOCR 首次运行会自动下载模型（约 300MB），请耐心等待
支持图片格式：jpg/png/jpeg，建议单张图片大小不超过 5MB
生成的 Word 文档默认字体为宋体 12 号，无需手动调整
该项目仅用于学习交流，禁止商用
常见问题（FAQ）
Q1：启动时提示「Using CPU」？
A1：正常现象！无 GPU 也可运行，仅识别速度稍慢，不影响功能使用。
Q2：访问 http://127.0.0.1:8000 报 404？
A2：需访问带 /docs 后缀的地址：http://127.0.0.1:8000/docs，这是 FastAPI 的可视化接口页面。
Q3：生成的 Word 文档乱码？
A3：代码已默认设置 UTF-8 编码和宋体字体，若乱码可：
打开 Word → 文件 → 选项 → 高级 → 编码 → 选择「UTF-8」
手动设置文档字体为宋体
Q4：API 调用失败 / 提示余额不足？
A4：
检查 .env 中的 API Key 是否正确
智谱免费模型需账号有余额（充值 1 元即可，不扣费）
确保网络正常，国内用户无需翻墙
