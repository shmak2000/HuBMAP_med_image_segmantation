# HuBMAP Medical images instance segmentation
Instance segmentation of histology images from human kidney tissue slides<br>
The data is from taken from a kaggle [competition](https://www.kaggle.com/competitions/hubmap-hacking-the-human-vasculature/overview/evaluation), the goal is to segment instances of microvascular structures on a histology images.<br><br>
Project starts with [Data preprocess/analysis notebook]('Data_preprocess_analysis.ipynb'), in wich methods for data reconstruction, analysis and image augmentation are presented.<br>

<img width="800" alt="data_sample" src="https://github.com/shmak2000/HuBMAP_med_image_segmantation/assets/109681522/57db6a57-d873-495f-88a3-941260edbe6a">

For main model I used UNet architecture with pre-trained Mix Vision Transformer (backbone from SegFormer) as an encoder. In the second notebook - 'WSI reconstruction' you can find model training and CV score estimation with K-fold CV method.<br><br>
I tried different encoder models like ResNet34, ResNet101, VGG16, DenseNet etc., the best results I got with Vision Transformer model.<br>
For the last model evaluation results, check the [Model evaluation notebook]("Model_evaluation.ipynb").<br>
Initial CV scoring got me target class IoU=0.33.<br>

<img width="800" alt="cv_score_initial" src="https://github.com/shmak2000/HuBMAP_med_image_segmantation/assets/109681522/9e1a64d1-54aa-4460-9cba-08c2dfe5ea27">

After hyperparameter tuning, using L2 and Dropout regularization, I got mean score around 0.4.<br>

<img width="800" alt="cv_score_fin" src="https://github.com/shmak2000/HuBMAP_med_image_segmantation/assets/109681522/baf29524-0682-4760-81f1-e96d66117464">

To separate every instance of target class, I used the Connected components method.
