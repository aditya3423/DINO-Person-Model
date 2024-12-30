The smaller version of the IIT Delhi dataset on pedestrians contains 200 images, which have been annotated in COCO format, with the corresponding annotations present in a JSON file.

First, the dataset is imported into Google Colab after being uploaded to Google Drive. The dataset is then visualized with bounding box annotations for a few images. The dataset is split into training and validation sets in a ratio of 80:20, or 160 images for the training set and 40 images for the validation set. The images are chosen randomly to be assigned to either the training or validation set, and their corresponding annotation JSON files are created. The entire training and validation sets are saved in the format required by the DINO model as shown below.
    COCODIR/
      ├── train2017/
      ├── val2017/
      └── annotations/
      	├── instances_train2017.json
      	└── instances_val2017.json

Next, the DINO repository is cloned to Google Drive, along with a saved checkpoint, which will be used to train the model.

After following the required steps to clone and set up the DINO repository, a modification is made in the cocoeval.py file, located in pycocotools, specifically at lines 378 and 379. The change involves updating 'np.float' to 'np.float64' or 'float', or alternatively, updating the pycocotools package.

Then, the evaluation of the DINO model on the dataset yields the following results:

    Average Precision (AP) @[ IoU=0.50:0.95 | area=all | maxDets=100 ] = 0.487
    Average Precision (AP) @[ IoU=0.50 | area=all | maxDets=100 ] = 0.841
    Average Precision (AP) @[ IoU=0.75 | area=all | maxDets=100 ] = 0.509
    Average Precision (AP) @[ IoU=0.50:0.95 | area=small | maxDets=100 ] = 0.409
    Average Precision (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.551
    Average Precision (AP) @[ IoU=0.50:0.95 | area=large | maxDets=100 ] = 0.822
    Average Recall (AR) @[ IoU=0.50:0.95 | area=all | maxDets=1 ] = 0.110
    Average Recall (AR) @[ IoU=0.50:0.95 | area=all | maxDets=10 ] = 0.505
    Average Recall (AR) @[ IoU=0.50:0.95 | area=all | maxDets=100 ] = 0.593
    Average Recall (AR) @[ IoU=0.50:0.95 | area=small | maxDets=100 ] = 0.536
    Average Recall (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.649
    Average Recall (AR) @[ IoU=0.50:0.95 | area=large | maxDets=100 ] = 0.860

After training the DINO model for 11 epochs, each checkpoint is saved to Google Drive, including the best checkpoint. The evaluation results after the final epoch are as follows:

    Average Precision (AP) @[ IoU=0.50:0.95 | area=all | maxDets=100 ] = 0.288
    Average Precision (AP) @[ IoU=0.50 | area=all | maxDets=100 ] = 0.564
    Average Precision (AP) @[ IoU=0.75 | area=all | maxDets=100 ] = 0.274
    Average Precision (AP) @[ IoU=0.50:0.95 | area=small | maxDets=100 ] = 0.211
    Average Precision (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.401
    Average Precision (AP) @[ IoU=0.50:0.95 | area=large | maxDets=100 ] = 0.470
    Average Recall (AR) @[ IoU=0.50:0.95 | area=all | maxDets=1 ] = 0.083
    Average Recall (AR) @[ IoU=0.50:0.95 | area=all | maxDets=10 ] = 0.387
    Average Recall (AR) @[ IoU=0.50:0.95 | area=all | maxDets=100 ] = 0.565
    Average Recall (AR) @[ IoU=0.50:0.95 | area=small | maxDets=100 ] = 0.484
    Average Recall (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.677
    Average Recall (AR) @[ IoU=0.50:0.95 | area=large | maxDets=100 ] = 0.753

The model was then setup to show the outputs on few images as shown below.

![1](https://github.com/user-attachments/assets/faf60ad2-c2e2-4055-9ac3-e6846fed9167)
![2](https://github.com/user-attachments/assets/3be6183e-e4a6-483f-9bfc-bb7daaeea1ed)

