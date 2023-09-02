# HuBMAP Medical images instance segmentation
Instance segmentation of histology images from human kidney tissue slides<br>
This one is a kaggle [competition](https://www.kaggle.com/competitions/hubmap-hacking-the-human-vasculature/overview/evaluation).<br>
My notebooks with data preprocessing, augmentation, models training + valuation. Valuation is like one in the competition -
target class IoU over confidence score for every instance.</br> My **general pipeline** goes like this - ensemble model, consisting of 3 UNet models with different backbones -
ResNet34, ResNet18 and Mix Vision Transformer (backbone from SegFormer). Models each are pretrained on imagenet, fine-tuned on labeled competition dataset and than fine-tuned on
unlabeled part of the dataset with pseudo labels.<br> UNet models do predict semantic segmentation masks, wich are then split into instance masks via ConnectedComponents.
