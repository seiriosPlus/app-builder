# AI作画-高级版 (Text2Image)

## 简介
AI作画-高级版（Text2Image）基于文心大模型，可以根据用户输入的文本，自动创作不限定风格的图，为内容创作者提供灵感和高质量配图。

### 功能介绍
AI一下，文字成画，AI 精准理解中文文本，支持用户自由输入，只需一句话，让文字秒变精美画作，支持自定义丰富的修饰词，可生成不同风格、不同构图、不同流派的图片，满足个性化的图片生成需求。
### 特色优势
利用知识增强扩散模型，学习过程融入语言、视觉、跨模态等多源知识，生成图像语义一致性更高，基于混合降噪专家网络，全球最大跨模态生成模型，参数规模达到240亿，根据生成阶段选择最优生成“专家”，从图像轮廓渐进优化细节，全面提升生成质量。
### 应用场景
图片素材、艺术插图、海报制作、故事插图、壁纸制作、电商应用、室内设计、影视制作、游戏原画设计、服务创意启发平台等。

## 基本用法

下面是AI作画的代码示例: 

```python
import os
import appbuilder
# 设置环境变量和初始化
# 请前往千帆AppBuilder官网创建密钥，流程详见：https://cloud.baidu.com/doc/AppBuilder/s/Olq6grrt6#1%E3%80%81%E5%88%9B%E5%BB%BA%E5%AF%86%E9%92%A5
os.environ["APPBUILDER_TOKEN"] = "..."

text2Image = appbuilder.Text2Image()
content_data = {"prompt": "上海的经典风景", "width": 1024, "height": 1024, "image_num": 1}
msg = appbuilder.Message(content_data)
out = text2Image.run(msg)
print(out.content)
```

## 参数说明

### 鉴权配置
使用组件之前，请首先申请并设置鉴权参数，可参考[使用流程](https://cloud.baidu.com/doc/AppBuilder/s/Olq6grrt6#1%E3%80%81%E5%88%9B%E5%BB%BA%E5%AF%86%E9%92%A5)。
```python
# 设置环境中的TOKEN，以下示例略
os.environ["APPBUILDER_TOKEN"] = "bce-YOURTOKEN"
```

### 初始化参数

无

### 调用参数
|参数名称 |参数类型 |是否必须 |描述 | 示例值    |
|--------|--------|--------|----|--------|
|message |String  |是 |输入的消息，输入的消息，用于模型的主要输入内容。这是一个必需的参数| Message(content={"prompt": "上海的经典风景"}) |
|width|Integer|是 |图片宽度，支持：512x512、640x360、360x640、1024x1024、1280x720、720x1280、2048x2048、2560x1440、1440x2560。| 1024   |
|height|Integer|是 |图片高度，支持：512x512、640x360、360x640、1024x1024、1280x720、720x1280、2048x2048、2560x1440、1440x2560。| 1024   |
|image_num|Integer|是 |生成图片数量，默认一张，支持生成 1-8 张。| 1      |
|timeout| Float   | 否    | HTTP超时时间,单位：秒               |1||
|retry|Integer|是 |HTTP重试次数| 3      |

### 响应参数
|参数名称 |参数类型 |描述 |示例值|
|--------|--------|----|------|
|result  |String  |返回结果|["xxx"]|

### 响应示例
```json
{"img_urls": ["xxx"]}
```
### 错误码
| 错误码 |描述|
|---|---|
| 282000 |服务器内部错误，请再次请求， 如果持续出现此类错误，请在控制台提交工单联系技术支持团队|
| 282004 |请求中包含敏感词、非法参数、字数超限，或上传违规参考图，请检查后重新尝试|
| 282003 |缺少必要参数|
| 17 |日配额流量超限|
| 18 |QPS 超限额|
| 216630 |服务器内部错误，请再次请求，如果持续出现此类错误，请通过工单联系技术支持|
| 501 |文本黄反拦截|
| 201 |模型生图失败|
| 216100 |参数不满足格式要求|
| 216201 |参考图不满足格式要求|
| 4 |错误信息为中文的“请求超限”指所有用户提交的 AI 作画总数超限制|
| 13 |错误信息为中文的“QPS 超限”指单个用户使用提交请求接口的 QPS 超限|
| 15 |错误信息为中文的“并发超限”指单个用户使用 AI 作画的并发超限|
| 17 |错误信息为中文的“用量超限”指单个用户使用 AI 作画的用量超限|



## 高级用法

目前该模块仅提供基础的AI作画功能。
## 更新记录和贡献
* AI作画能力 (2023-12)