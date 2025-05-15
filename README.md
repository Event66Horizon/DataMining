# DataMining
环境要求
Python 3.7 及以上版本
已安装以下依赖：
numpy
pandas
torch
transformers
scikit-learn
matplotlib
tqdm
chardet
peft (安装方式: pip install peft)
文件说明
Fake_Real_News_torch_RoBERTa+PEFT.ipynb：主程序。主要包含以下步骤：
读取数据并合并 (fake, true)
将文本和标签映射为模型可处理的形式
使用 RoBERTa + LoRA (PEFT) 对数据进行训练和验证
输出验证、可视化结果并进行测试预测
如何更换数据文件
在当前目录下准备两份 CSV 文件，名称与代码里引用的相同 (如：sampled_fake.csv 与 sampled_true.csv) ，或者修改代码中的读取路径：
fake = pd.read_csv('你的假新闻文件.csv')
true = pd.read_csv('你的真新闻文件.csv')
确保这些 CSV 文件内至少包含名为 “text” 的文本列，用来做模型输入。
运行步骤
克隆或下载包含所有文件的工作目录到本地。
打开 Fake_Real_News_torch_RoBERTa+PEFT.ipynb (可以使用 VSCode 或 Jupyter Notebook)。
或者逐一安装对应包（如：pip install numpy pandas torch transformers scikit-learn matplotlib tqdm chardet peft）。
根据需要修改以下参数：
debug / debug2：布尔值，控制是否进行完整训练
文件读取名字或路径
训练轮数（epochs）
批量大小（train_batch, valid_batch, 等）
在 notebook 中依次顺序执行每个单元格，代码会：
加载并处理数据
对 RoBERTa 模型进行部分参数微调 (LoRA)
进行训练、验证、可视化以及最终预测
训练完成后，程序会输出训练及验证的相关指标，并在本地生成模型文件 “model0.pth” 等。
注意事项
如果出现显存不足，可以调低 batch_size 或 max_sens，或者减少模型规模。
如果仅想迅速测试代码的流程，可将 debug = True 以便跳过完整训练，了解整体运行过程。
若需要使用完整 K 折验证，会有更多的训练轮次，否则可以跳过该部分。
无论是ROBERTA还是ROBERTA+PEFT对于上述运行方法都是一样
