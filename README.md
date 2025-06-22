# 大语言模型部署体验

## 项目简介
本项目为《2025人工智能导论》课程第四次作业，通过在ModelScope平台部署多个开源大语言模型，进行本地推理测试和模型性能对比分析。项目包含完整的部署流程指南、测试脚本和模型对比报告。

## 作业要求
1. 在ModelScope平台部署2-3个大语言模型
2. 进行问答场景测试并记录结果
3. 完成模型横向对比分析
4. 提交包含以下内容的报告：
   - Git clone或部署完成截图
   - 问答测试结果截图
   - 模型对比分析（推理速度、回答质量等）

## 部署流程

### 1. 环境准备

# 安装基础依赖
pip install torch==2.3.0+cpu torchvision==0.18.0+cpu \
  --index-url https://download.pytorch.org/whl/cpu

# 安装LLM部署依赖
pip install intel-extension-for-transformers==1.4.2 \
  neural-compressor==2.5 \
  transformers==4.33.3 \
  modelscope==1.9.5 \
  fschat --use-pep517


### 2. 下载模型

cd /mnt/data

# 通义千问
git clone https://www.modelscope.cn/qwen/Qwen-7B-Chat.git

# 智谱ChatGLM
git clone https://www.modelscope.cn/ZhipuAI/chatglm3-6b.git

# 百川模型
git clone https://www.modelscope.cn/baichuan-inc/Baichuan2-7B-Chat.git


### 3. 推理脚本示例

见仓库内run_model.py文件

### 4. 运行测试

python run_inference.py


## 测试问题示例
1. 请说出以下两句话区别在哪里？  
   - 冬天：能穿多少穿多少  
   - 夏天：能穿多少穿多少

2. 单身狗产生的原因有两个，一是谁都看不上，二是谁都看不上

3. 他知道我知道你知道他不知道吗？这句话里，到底谁不知道

4. 明明明明明白白白喜欢他，可她就是不说。 这句话里，明明和白白谁喜欢谁？

5. 领导：你这是什么意思？小明：没什么意思。意思意思。  
   领导：你这就不够意思了...（分析所有"意思"的含义）

## 模型对比维度
| 评估指标       | 说明                  |
|---------------|-----------------------|
| 响应速度       | 生成答案所需时间       |
| 回答准确性     | 对歧义问题的理解能力   |
| 中文语义理解   | 对中文双关语的解析     |
| 推理能力       | 逻辑链条的完整性       |


## 推荐开源模型
1. [通义千问Qwen-7B-Chat](https://www.modelscope.cn/models/qwen/Qwen-7B-Chat/summary)
2. [智谱ChatGLM3-6B](https://www.modelscope.cn/models/ZhipuAI/chatglm3-6b/summary)
3. [百川2-7B-对话模型](https://www.modelscope.cn/models/baichuan-inc/Baichuan2-7B-Chat/summary)

## 报告要求
1. 部署过程截图（3分）
2. 问答测试结果截图（3分）
3. 模型对比分析（6分）
   - 响应速度对比
   - 回答质量评估
   - 资源消耗比较
   - 综合推荐建议

## 注意事项
⚠️ CPU资源1小时未使用会自动释放  
⚠️ 一次只下载一个模型避免存储不足  
⚠️ 及时保存重要数据到持久化存储