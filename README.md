# Transformer Diacritization
Arabic diacritization with self-attention Transfromers. The task is a sequence labeling task where the goal is to label each character with its correct diacritic.

### Getting Started

```
# clone repo
git clone https://github.com/mohammadKhalifa/transformer-diacritization.git`

# download dataset
cd transformer-diacritization/
wget https://sourceforge.net/projects/tashkeela/files/latest/download

mv download tashkeela.zip
mkdir data
unzip -q tashkeela.zip -d data/
mv data/Tashkeela-arabic-diacritized-text-utf8-0.3/ data/tashkeela 
rm data/tashkeela/doc/ -r 

# preparing dataset
python scripts/preprocess_data.py --corpus data/tashkeela/texts.txt/
python scripts/prepare_diacritization_dataset.py --corpus-dir data/preprocessed --outdir data/tashkeela/bin
```


### Training
I trained a 10-layer transformer model using the following parameters:


```python

#Model Params

embedding_dim = 512
hidden_dim = 512
num_max_positions = 256
num_attention_heads = 8
num_layers = 10
dropout = 0.1
batch_size = 64
lr = 0.0001

#Training Params

epochs=10
max_norm = 5.0
gradient_accumulation_steps= 4
batch_size=64
```

![loss](figures/loss_epoch4.png)

![acc](figures/acc_epoch4.png)



