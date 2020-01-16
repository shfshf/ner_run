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

### gpu，指定显卡运行(针对多显卡)
```
# 选择 estimator 模型进行训练
CUDA_VISIBLE_DEVICES=0 python -m ner_s2s.ner_estimator.estimator_run

# 选择 keras 模型进行训练
CUDA_VISIBLE_DEVICES=1 python -m ner_s2s.ner_keras.keras_run
```

## add
如果想要深入理解具体的执行库函数代码，见我的 github 项目[*ner_s2s*](https://github.com/shfshf/ner_s2s)