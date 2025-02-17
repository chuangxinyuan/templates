# 内置工作流模板、内置工作区模版、sidecar和任务
上海仪电人工智能创新院AI中台(以下简称AIMP）中内置工作流、内置工作区的模板目录。用户可以直接使用工作流、工作区，或者基于该模板修改，开发自己的工作流或者工作区。

## 快速上手
入门最好先了解 AIMP 的[概念](https://docs.dev.aimpcloud.cn)。

有关如何构建这些模板的更多信息，请参阅以下参考资料：

- [工作区管理](https://docs.dev.aimpcloud.cn/docs/reference/workspaces/templates)
- [工作流管理](https://docs.dev.aimpcloud.cn/docs/reference/workflows/templates)

## 目录概览

### 内置工作流模板
内置工作流模板由 YAML 定义和在 AIMP 中定义 DAG 的 Docker 映像组成。

📍如下内置工作流模板已经测试通过，并且可以在 AIMP 中部署。 

📍在部署如下内置工作流模板时，可以把github 替换为gitee，以获得更好的连接速度
|内置工作流模板YAML文件位置|AIMP中内置工作流模板名称|描述|执行位置|备注|
| ------------- | ------------- | ------------- | ------------- | ------------- |
|✔[example models serving test](https://github.com/chuangxinyuan/aimp-examples/tree/master/aimp-serving)|aimp-serving-examples|参考 aimp-serving-test-flow.yaml，运行 aimp-serving-examples 内置工作流，选择 sample-name 下面的模型，然后执行，可以从流日志中查看相应的执行效果|在AIMP中直接执行该内置工作流||
|✔[Hyperparameter tuning](https://github.com/chuangxinyuan/templates/blob/master/workflows/hyperparameter-tuning)|Hyperparameter Tuning Example|超参数优化内置工作流使用 [NNI](https://github.com/microsoft/nni)，并包含在 AIMP 部署中。 超参数调优任务之后是 Metrics Writer 任务，因此您可以在任务信息窗格的 Artifacts 下查看最佳模型性能指标。 | 在AIMP中直接执行该内置工作流||
|✔[PyTorch training](https://github.com/chuangxinyuan/templates/blob/master/workflows/pytorch-mnist-training)|PyTorch Training|使用PyTorch训练MNIST手写体识别的简单示例。 模型训练任务之后是 Metrics Writer 任务，因此您可以在任务信息窗格的 Artifacts 下查看模型性能指标。包含在 AIMP 部署中。| 在AIMP中直接执行该内置工作流|
|*✔[TensorFlow Object Detection training](https://github.com/chuangxinyuan/templates/blob/master/workflows/tf-object-detection-training) |TF Object Detection Training|目标检测模型训练的内置工作流程与 CVAT 完全集成并包含在 AIMP 部署中。 pip 源已更改为清华源。 包含在 AIMP 部署中。| 内置内置工作流，参考[最佳实践](https://docs.dev.aimpcloud.cn/docs/bestsample/overview)中的案例执行||
|*✔[license-plate-detection](https://github.com/chuangxinyuan/LicensePlateOcr) |license-plate-detection|此内置工作流中，将使用车牌检测和车牌识别 (OCR) 的示例来演示 AIMP 如何帮助您简化在 Kubernetes 上构建易于扩展和可迁移的深度学习内置工作流的过程。|内置内置工作流，参考[最佳实践](https://docs.dev.aimpcloud.cn/docs/bestsample/overview)中的案例执行||
|*✔[Ensemble Multiple Models Demo](https://github.com/chuangxinyuan/ensembleObjectDetection) |Ensemble Multiple Models Demo|此示例以一个集成推理的例子作为演示。在这里，我们将使用多个目标检测模型来生成推理结果，然后使用集成策略得出最终输出。|内置内置工作流，参考[最佳实践](https://docs.dev.aimpcloud.cn/docs/bestsample/overview)中的案例执行|增加 used-by:cvat 标签|

以下内置工作流模板未经测试：
- [Albumentations data pre-processing](https://github.com/chuangxinyuan/templates/blob/master/workflows/albumentations-preprocessing) - 此内置工作流包含在 [TFOD](https://github.com/chuangxinyuan/templates/tree/release-v0.18.0/workflows/tf-object-detection-training) 以及 [MaskRCNN](https://github.com/chuangxinyuan/templates/tree/release-v0.18.0/workflows/maskrcnn-training) 训练内置工作流，并允许您在训练之前对数据应用不同的增强。
- [Auto CVAT](https://github.com/chuangxinyuan/templates/blob/master/workflows/auto-cvat) - 允许您通过创建 CVAT 实例并使用要标注的数据预填充它们来自动化标注内置工作流。
- [MaskRCNN training](https://github.com/chuangxinyuan/templates/blob/master/workflows/maskrcnn-training) - 语义分割模型训练的内置工作流与 CVAT 完全集成并包含在 AIMP 部署中。
- [TensorFlow training](https://github.com/chuangxinyuan/templates/blob/master/workflows/tensorflow-mnist-training) - 使用 TensorFlow 的简单 MNIST 训练示例。

### 内置工作区模板
内置工作区模板由 YAML 定义和定义有状态实例的 Docker 映像组成，例如 JupyterLab、CVAT 和其他常用工具。

📍如下内置工作区模板已经测试通过，并且可以在AIMP中部署。  
|内置工作区模板YAML文件位置|AIMP中内置工作区模板名称|描述|执行位置|
| ------------- | ------------- | ------------- | ------------- |
|✔[CVAT](https://github.com/chuangxinyuan/templates/blob/master/workspaces/cvat)|CVAT*|用于计算机视觉的交互式视频和图像注释工具。| AIMP中直接执行|
|✔[CVAT](https://github.com/chuangxinyuan/templates/blob/master/workspaces/cvat)|CVAT_1.6.0**|用于计算机视觉的交互式视频和图像注释工具。| AIMP中直接执行|
|✔[JupyterLab](https://github.com/chuangxinyuan/templates/blob/master/workspaces/jupyterlab)|JupyterLab|基于 Jupyter Notebook 的交互式和可重复计算的可扩展环境。| AIMP中直接执行|

\* CVAT 目前支持的上传标注格式有限，如果希望获得更完整的上传数据标注功能体验，建议选择 CVAT_1.6.0 模板。

\** CVAT_1.6.0 目前自动标注功能还在开发中，如果希望使用自动标注功能，建议选择 CVAT 模板。

以下内置工作流模板未经测试：
- [Eclipse Theia](https://github.com/chuangxinyuan/templates/blob/master/workspaces/theia) - 一个可扩展的平台，用于使用最先进的 Web 技术开发多语言云和桌面 IDE。
- [Ubuntu VNC](https://github.com/chuangxinyuan/templates/blob/master/workspaces/vnc) (alpha) - 可在您的 Web 浏览器中访问的完整 Ubuntu 实例。
- [Visual Studio Code](https://github.com/chuangxinyuan/templates/blob/master/workspaces/vscode) - 一个轻量级但功能强大的源代码编辑器，几乎支持所有内容。

### 边车
边车是扩展您的内置工作区或内置工作流任务的组件。

- [FileSyncer 文件同步器](https://github.com/chuangxinyuan/templates/blob/master/sidecars/filesyncer) - 提供用于在内置工作区和默认对象存储之间同步文件的 API。
- [NNI Web UI](https://github.com/chuangxinyuan/templates/blob/master/sidecars/nni-web-ui) - 为 NNI Web UI 提供代理，以便您可以查看超参数调整内置工作流中的实验。

### 任务
任务是内置工作流中的单个任务（DAG 中的节点）。

- [Metrics writer](https://github.com/chuangxinyuan/templates/blob/master/tasks/metrics-writer) - 您可以包含在任何内置工作流模板中以保留最终指标的任务。
