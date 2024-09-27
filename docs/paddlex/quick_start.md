# PaddleX快速开始
PaddleX的各个产线均支持**在线体验**和本地**快速推理**，您可以快速体验各个产线的预训练效果，如果您对产线的预训练效果满意，可以直接对产线进行[高性能部署](/docs/paddlex/pipeline_deploy/high_performance_deploy.md)/[服务化部署](./pipeline_deploy/service_deploy.md)/[端侧部署](./pipeline_deploy/lite_deploy.md)，如果不满意，您也可以对产线进行**二次开发**提升产线效果。完整的产线开发流程请参考[PaddleX产线开发工具本地使用教程](./pipeline_usage/pipeline_develop_guide.md)。

此外，PaddleX为开发者提供了基于[云端图形化开发界面](https://aistudio.baidu.com/pipeline/mine)的全流程高效模型训练与部署工具。开发者**无需代码开发**，只需要准备符合产线要求的数据集即可**快速启动模型训练**,详细请参考[教程《零门槛开发产业级AI模型》](https://aistudio.baidu.com/practical/introduce/546656605663301)

## ⏭️ 快速开始

### 🛠️ 安装

> ❗安装PaddleX前请先确保您有基础的Python运行环境，如果您还未安装Python环境，可以参考[运行环境准备](./installation.md)进行安装

```bash
# 您的机器安装的是CUDA 11，请运行以下命令安装
pip install paddlepaddle-gpu
# 您的机器是CPU，请运行以下命令安装
pip install paddlepaddle
...
```
  
更多安装方式参考[PaddleX安装教程](./installation.md)

### 💻 命令行使用

一行命令即可快速体验产线效果，以通用OCR产线为例：
```bash
paddlex --pipeline image_classification --input https://paddle-model-ecology.bj.bcebos.com/paddlex/imgs/demo_image/garbage_demo.png --device gpu:0
```

只需指定三个参数：
* `pipeline`：产线名称
* `input`：待处理的输入图片的本地路径或URL
* `device`: 使用的GPU序号（例如`gpu:0`表示使用第0块GPU），也可选择使用CPU（`cpu`）



其他产线的命令行使用，只需将`pipeline`参数调整为相应产线的名称。下面列出了每个产线对应的参数名称及详细的使用解释：

<details>
  <summary>👉 更多产线的命令行使用</summary>

| 产线名称     | 对应参数                 | 详细说明 |
|----------|----------------------|------|
| 通用OCR产线 | `OCR` |   [通用OCR产线命令行使用说明](./pipeline_usage/OCR.md#221-命令行方式体验)   |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |

</details>

### 📝 Python脚本使用

几行代码即可完成产线的快速推理，以通用OCR产线为例：
```python
from paddlex import create_pipeline

pipeline = create_pipeline(pipeline="ocr")
output = pipeline.predict("pre_image.jpg")
for batch in output:
    for item in batch:
        res = item['result']
        res.print()
        res.save_to_img("./output/")
        res.save_to_json("./output/")
```
执行了如下几个步骤：

* `create_pipeline()` 实例化产线对象
* 调用产线对象的`predict` 方法进行推理预测
* 对预测结果进行处理

其他产线的Python脚本使用，只需将`create_pipeline()`方法的`pipeline`参数调整为相应产线的名称。下面列出了每个产线对应的参数名称及详细的使用解释：
<details>
  <summary>👉 更多产线的Python脚本使用</summary>
  
  | 产线名称     | 对应参数                 | 详细说明 |
|----------|----------------------|------|
| 通用OCR产线 | `OCR` |   [通用OCR产线Python脚本使用说明](./pipeline_usage/OCR.md#222-python脚本方式集成)   |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |
|          |                      |      |

</details>