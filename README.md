# ner_s2s执行文件

在根目录中必须要的二个文件
* data文件夹，用来存放数据集
* configure.yaml, 设定配置超参数以及文件输入输出的路径

```
# 直接通过pip安装

pip install -U ner-s2s
```

## 在terminal中执行

### cpu
```
# 选择 estimator 模型进行训练
python -m ner_s2s.ner_estimator.estimator_run

# 选择 keras 模型进行训练
python -m ner_s2s.ner_keras.keras_run
```

### gpu，指定显卡运行(针对多显卡)
```
# 选择 estimator 模型进行训练
CUDA_VISIBLE_DEVICES=0 python -m ner_s2s.ner_estimator.estimator_run

# 选择 keras 模型进行训练
CUDA_VISIBLE_DEVICES=1 python -m ner_s2s.ner_keras.keras_run
```