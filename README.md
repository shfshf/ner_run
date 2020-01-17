# ner_s2s执行文件

## 本项目是命名实体识别（NER）模型的执行文件

在根目录中必须要的二个文件（也只需要这两个）
* data文件夹，用来存放数据集
* configure.yaml, 设定配置超参数以及文件输入输出的路径

在新建的 conda 环境中（python=3.6），只需要安装 ner-s2s 这个库即可；

(因为这个库包含了所需要的全部依赖)
```
# 直接通过pip安装

pip install -U ner-s2s
```

## 然后在terminal中执行命令

### cpu
```
# 选择 estimator 模型进行训练
python -m ner_s2s.ner_estimator.estimator_run

# 选择 keras 模型进行训练
python -m ner_s2s.ner_keras.keras_run
```

### gpu

这里需要说明的是，通过`pip install -U ner-s2s`安装所需的依赖在服务器上的conda环境中，
是无法直接使用gpu训练模型的，需要在conda环境中安装 nvidia 相关的 cudnn 驱动；

怎样查看 conda 环境是否可以使用gpu加速？三步：
* `python` 进入命令行模式
* `import tensorfow as tf` 导入tensorflow
* `tf.test.is_gpu_available()` 如果显示 True 则大功告成

所以需要在 conda 环境中多安装一次 gpu 驱动：
```
conda install tensorflow-gpu==1.15
```

然后指定显卡运行(针对多显卡)即可：
```
# 选择 estimator 模型进行训练
CUDA_VISIBLE_DEVICES=0 python -m ner_s2s.ner_estimator.estimator_run

# 选择 keras 模型进行训练
CUDA_VISIBLE_DEVICES=1 python -m ner_s2s.ner_keras.keras_run
```

## add
如果想要深入理解具体的执行库函数代码，见我的 github 项目[*ner_s2s*](https://github.com/shfshf/ner_s2s)