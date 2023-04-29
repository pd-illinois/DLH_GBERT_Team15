## Final Project: 

Reproducibility Project: Pre-training of Graph Augmented Transformers for Medication Recommendation

## Project Team: 

Prateek Dhiman : pdhiman2@illinois.edu

Unnati Hasija : uhasija2@illinois.edu

## Steps to replicate/Reproducibility:

## 1. Dependencies:

To reproduce the results or to be able to execute the G-Bert code, we were missing some libraries. We created a list of those libraries in requirements.txt.
You may install it using:
$ pip install -r requirements.txt

## 2. Training code:

The dataset is split into training, validation and testing set in ratio of 0.6,0.2,0.2 respectively. The split is done in EDA.ipynb file train-id.txt, eval-id.txt, test-id.txt 
and the files are stored accordingly.
The script for training the G-Bert model is provided in run_alternative.sh bash script. The script basically executes the pretraining.py to pretrain the G-Bert on EHR Data.
Then it executes the G-Bert prediction on this pre-trained model. The script alternates the pre-training with 5 epochs and fine-tuning procedure with 5 epochs for 15 times to stabilize the training procedure.
For our project, we adjusted the above script to execute pre-training with and without graphs and with and without pre-training.
We also executed the script after changing the GAT model to GCN and GTN to test our ablations.

# 3. Evaluation code 

We evaluated the results by executing:
python run_gbert.py --model_name GBert-predict --use_pretrain --pretrain_dir ../saved/GBert-predict --graph

# 4. Pre-training and pre-trained models:

In the run_pretraining.py, BERT model pre-trained on the EHRDataset (both single-visit EHR sequences and multi-visit EHR sequences). 
In here, the 15% of the tokens are replaced by [MASK] and [CLS] is the first token of each sentence. 
The pre-training code creates a model with the config specified in config.py.

# Baselines and ablations:

To prove the claims and ablations in the original paper and to test our ablations, we took the baselines as follows:
We used local CPU and on GPU - 1 x NVIDIA Tesla K80: Standard_NC6 (6 cores, 56 GB RAM, 380 GB disk).

# Baselines:
<insert the table here>

## ** Ablations: **
  
<insert the table here>


# Citation
@article{shang2019pre,
  title={Pre-training of Graph Augmented Transformers for Medication Recommendation},
  author={Shang, Junyuan and Ma, Tengfei and Xiao, Cao and Sun, Jimeng},
  journal={arXiv preprint arXiv:1906.00346},
  year={2019}
}
