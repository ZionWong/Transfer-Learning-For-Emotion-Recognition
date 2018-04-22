### 1、工程目录说明
- feature ：存储Opensmile得到的988维语音情感向量
- origin_data ：存储Opensmile得到的.arff文件
- transfer_feature ：存储由稀疏自编码器经过特征迁移后得到的变换特征
- autoencoder.ipynb ：构建稀疏自编码器并进行特征迁移的代码
- classifier.ipynb ： 最后对特征迁移后的数据进行分类的代码，为一个DNN模型，可自行用其他模型替换
- feature_extraction.ipynb ：对.arff文件进行特征提取的代码
- README.md

### 2、使用说明
- 首先运行feature_extraction.ipynb，其会在feature文件夹中生成988维特征向量文件
- 接下来运行autoencoder.ipynb，其中构建了一个5层稀疏自编码器，并进行了特征迁移，得到特征迁移后的变化特征
- 最后运行classifier.ipynb，对迁移特征进行分类，得到最终迁移学习的性能评估指标。

### 3、进行其他数据库实验说明
- 其他数据库的.arff文件请放在origin_data路径下，内层路径可自行设置，并在feature_extraction.ipynb文件中进行对应的修改
- 运行autoencoder.ipynb时需要注意，由于稀疏自编码器的构建、训练以及之后的特征迁移均在该代码文件中完成，如果使用的是jupyter noteboook，建议将训练和特征迁移分块运行，__优先自编码器的训练，即对自编码器进行参数调整并训练，得到最佳性能的自编码器之后再进行特征迁移__，否则效果不佳。如果使用的是.py类的IDE，则建议*将稀疏自编码器的训练和特征迁移拆分*，拆分为两个文件独立进行，先训练自编码器，并将自编码器进行保存，再用自编码器进行特征迁移。