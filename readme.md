# iNaturalist Competition Training Code

This code finetunes an Inception V3 model on the iNaturalist 2017 competition dataset. 
You can read about the results in [this](https://medium.com/@macaodha/inaturalist-2017-species-classification-challenge-4ff4d1499279) blog post.


### Training
The network was trained on Ubuntu 16.04 using PyTorch 0.1.12. Each training epoch took about two hours using a GTX 1080. 
The links for the raw data are available [here](https://github.com/visipedia/inat_comp).
We also provide a pretrained model that can be downloaded from [here](http://vision.caltech.edu/~macaodha/inat2017/iNat_2017_InceptionV3.pth.tar).
Every epoch the code will save a checkpoint and also save the current best model according to validation accuracy.


### Results
Training for about 70 epochs (note the model pretty much converges after 30 epochs) results in a top one accuracy of 64.44% and and top five of 85.34% on the validation set. 
Below are the results broken down by super category.

| Super Category |	Num Classes	| Val Top 5 Acc (%)|
|------|---------------|-------------|
Plantae|2,101|85.96|
Insecta|1,021|89.66|
Aves|964|85.40|
Reptilia|289|74.56|
Mammalia|186|79.48|
Fungi|121|89.44|
Amphibia|115|75.09|
Mollusca|93|83.00|
Animalia|77|85.39|
Arachnida|56|88.95|
Actinopterygii|53|79.90|
Chromista|9|81.94|
Protozoa|4|91.78|



### Submission File
By setting the following flags it's possible to generate a submission file for the competition. 
```python 
    evaluate = True
    save_preds = True
    resume = 'model_path/iNat_2017_InceptionV3.pth.tar'  # path to trained model
    val_file = 'ann_path/test2017_3_public_use.json'     # path to test file
    rootdir = 'test_ims_path/ignat_test_images_2017/'    # path to test images
    op_file_name = 'inat2017_test_preds.csv'             # submission filename
```

