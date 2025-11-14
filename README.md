# PyTorch3D Neural Surface Rendering (NSR) Training

这是一个基于PyTorch3D的神经表面渲染(NSR)训练系统。

## 环境配置

### 安装依赖

```bash
pip install -r requirements.txt
```

### 主要依赖项：

- **torch==1.13.0** - PyTorch框架
- **torchvision==0.14.0** - 视觉模型库
- **pytorch3d==0.7.5** - 3D计算机视觉库
- **PyYAML==6.0.3** - YAML配置文件解析
- **opencv_python==4.9.0.80** - 图像处理
- **numpy==2.3.4** - 数值计算
- **Pillow==12.0.0** - 图像处理
- **tensorflow==2.20.0** - TensorFlow框架
- **wandb==0.23.0** - 实验追踪和可视化
- **tqdm==4.66.2** - 进度条工具

完整的依赖列表见 `requirements.txt`。

## 使用方法
### 自定义数据集路径: ###

文件位置 `data/nsr.yaml`
修改 `path` 字段为你的数据集路径：

```yaml
path: /your/custom/dataset/path/
```



文件位置: `utils/datasets_NSR_pytorch3D.py`

在 `LoadImagesAndLabels` 类中修改 `data_root` 变量：

```python
# 第484行
data_root = "/data/zhoujw/DTN"  # 修改为你的数据集路径
```


### 命令行参数

运行训练脚本时使用以下参数：

```bash
python SimpleNSR_GPUS_mixedColor_Pytorch.py \
    --obj_file <path/to/model.obj> \
    --datapath <path/to/dataset> \
    --device <device_id> \
    --batch-size <batch_size>
```

#### 参数说明：

| 参数 | 类型 | 说明 | 示例 |
|------|------|------|------|
| `--obj_file` | str | **必需**。目标模型的OBJ文件路径 | `/path/to/model.obj` |
| `--datapath` | str | **必需**。数据集路径，包含训练数据 | `/data/zhoujw/DTN` |
| `--device` | int | **可选**。GPU设备ID (默认: 0) | `0` 或 `1` |
| `--batch-size` | int | **可选**。总batch_size大小 (默认值见config) | `32` |

### 完整示例

```bash
# 多GPU训练
python SimpleNSR_GPUS_mixedColor_Pytorch.py \
    --obj_file ./car_pytorch3d_last/model.obj \
    --datapath /data/zhoujw/DTN \
    --device '0,1,2,3' \
    --batch-size 16



## 参考资源

- [PyTorch3D官方文档](https://pytorch3d.org/)
- [YOLOv3官方项目](https://github.com/ultralytics/yolov3)
- [训练数据最佳实践](https://github.com/ultralytics/yolov3/wiki/Train-Custom-Data)

## 许可证

请查阅项目根目录的LICENSE文件。

---

**最后更新:** 2025年11月
