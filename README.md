# HuBMAP Medical images instance segmentation
Instance segmentation of histology images from human kidney tissue slides<br>
The data is from taken from a kaggle [competition](https://www.kaggle.com/competitions/hubmap-hacking-the-human-vasculature/overview/evaluation), the goal is to segment instances of microvascular structures on a histology images.<br><br>
Project starts with 'Data preprocess/analysis' notebook, in wich methods for data reconstruction, analysis and image augmentation are presented.<br>

<img width="800" alt="image" src="https://github.com/shmak2000/HuBMAP_med_image_segmantation/assets/109681522/57db6a57-d873-495f-88a3-941260edbe6a">

For main model I used UNet architecture with pre-trained Mix Vision Transformer (backbone from SegFormer) as an encoder. In the second notebook - 'WSI reconstruction' you can find model training and CV score estimation with K-fold CV method.<br><br>
Valuation is like one in the competition -
target class IoU over confidence score for every instance.</br> My **general pipeline** goes like this - ensemble model, consisting of 3 UNet models with different backbones -
ResNet34, ResNet18 and Mix Vision Transformer (backbone from SegFormer). Models each are pretrained on imagenet, fine-tuned on labeled competition dataset and than fine-tuned on
unlabeled part of the dataset with pseudo labels.<br> UNet models do predict semantic segmentation masks, wich are then split into instance masks via ConnectedComponents.
