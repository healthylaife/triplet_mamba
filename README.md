Implementation code for the paper "Triplet-Mamba: Mamba-based architecture for longitudinal representation learning and patient subtyping"
![Triplet_mamba](https://github.com/user-attachments/assets/edc5c3ff-1f79-4526-a366-5ef529bab0e8)

__Requirements:__

!pip install transformers

!pip install torcheval timm

!pip install causal-conv1d>=1.4.0

!pip install mamba-ssm

!pip install https://github.com/Dao-AILab/flash-attention/releases/download/v2.7.3/flash_attn-2.7.3+cu12torch2.6cxx11abiFALSE-cp310-cp310-linux_x86_64.whl

!pip install torch==2.5.1+cu121 torchvision==0.20.1+cu121 torchaudio==2.5.1+cu121 --index-url https://download.pytorch.org/whl/cu121

!pip install pandas==1.5.3

__To run pretraining:__

%run main.py --pretrain 1 --dataset physionet_2012 --model_type trimba --train_frac 1.0 --train_batch_size 32 --hid_dim 16 --num_layers 4 --num_heads 8 --dropout 0.2 --attention_dropout 0.2 --lr 5e-4 --max_epochs 100 --max_obs 1497

__For fine-tuning:__

%run main.py --pretrain 0 --dataset physionet_2012 --model_type trimba --train_frac 1.0 --train_batch_size 32 --hid_dim 16 --num_layers 4 --num_heads 8 --dropout 0.2 --attention_dropout 0.2 --lr 5e-4 --max_epochs 10 --load_ckpt_path ./outputs/physionet_2012/pretrain/checkpoint_best.bin --max_obs 1497
