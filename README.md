## 一、环境准备
### 1. 搭建Python虚拟环境（推荐Anaconda）
```bash
# 创建虚拟环境（Python 3.9兼容性最佳）
conda create -n ocr_word_env python=3.9
# 激活虚拟环境
conda activate ocr_word_env
2. 安装依赖包（一键执行）
bash
运行
pip install fastapi uvicorn python-multipart easyocr python-docx openai python-dotenv -i https://pypi.tuna.tsinghua.edu.cn/simple
二、配置步骤
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
三、启动与使用
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
