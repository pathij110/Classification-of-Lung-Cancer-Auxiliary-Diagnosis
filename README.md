
# Classification of Lung Cancer & Auxiliary Diagnosis

This project falls under the Data-Knights group. Its purpose is to provide further assessment of patients based on lung CT scans following lung cancer risk evaluation. The project's contributions are twofold: 1. Our innovative model achieved 96% accuracy on the test set, with recall rates approaching or reaching 100% for key diseases. To our knowledge, this model's performance is leading on the datasets used. 2. We provide functionality to generate feature maps for specified CT scans, offering clinicians clinical assessment criteria from five distinct perspectives.

Tec: Swin tran, Pathology CNN, Fusion Network, MLP, AdamW, Mixed-precision training, EMA, Focal Loss, Otsu algorithm, CLAHE, Guided Filter, Frangi Filter, Gabor Filter

## 🛠️ Demo
We have placed several images demonstrating the model's performance in the [here](https://pan.baidu.com/s/10R7X0PGnYauyZSSdWlBDww?pwd=2025). **Our results can be obtained from here, including metric calculations, confusion matrices, and representative pathological features of three types of diseased lungs and normal lungs.**

## 🔥 Note
1 . The team's expertise in **medical pathology is limited**, and we **welcome criticism and corrections** from experts.

2 . This model is designed for **aids to diagnosis** and **cannot replace professional judgement**.
## ⭐ Authors

-  @pathij110
-  @rainbowgoose-killer
-  @GroveLxx

## 🤝 Acknowledgements

 - [Swin Transformer](https://github.com/microsoft/Swin-Transformer)
 We are grateful for the pre-trained weights they have provided！🙏
 - [Chest CT-Scan images Dataset](https://www.kaggle.com/datasets/mohamedhanyyy/chest-ctscan-images)
 We are grateful for the dataset they have provided！🙏
 
 If you are already logged into Kaggle, you can obtain it via the following codes:
```bash
import kagglehub

# Download latest version
path = kagglehub.dataset_download("mohamedhanyyy/chest-ctscan-images")

print("Path to dataset files:", path)
```
 
 - @Ayakaze139
 - @yl2119
 - @ZuoeR-Pro

 We are grateful for other members for their support of our work！🙏
 

## 📂 Dataset Preparation
You may access our used datasets or utilise your own datasets. 

The datasets we have utilised are detailed in the acknowledgements section. If you have your own dataset, please ensure it is formatted as follows:

```bash
test_dataset/
├── Adenocarcinoma/
│   ├── image1.(jpg/png)
│   ├── image2.(jpg/png)
│   └── ...
├── Large_Cell/
├── Normal/
└── Squamous_Cell/
```

The optimal weights we have trained are provided [here](https://pan.baidu.com/s/10R7X0PGnYauyZSSdWlBDww?pwd=2025). 

Please just download it and place it in this directory.

## 🚀 Running Tests

We provide the CPU version, which appears more versatile and convenient to run.

Before running the test script, please ensure that the directories **./results** and **./eva_results** have been created.

First, we set up the environment:

```bash
conda create -n lung_cancer python=3.9
conda activate lung_cancer
pip install -r requirements.txt
```

Next, we shall test. Testing code operates in two modes. 

The **full_test** mode outputs the overall score of the test set to the console and outputs the confusion matrix to **./eva_results**. 

```bash
python test.py --mode full_test  \
  --test_data_root your_data_path \
  --checkpoint best_model_ema.pth \
  --save_dir ./eva_results \
  --batch_size 16 \
  --num_workers 0  
```

The **single** mode outputs the classification confidence level for a single specified CT to the console and outputs five feature maps to **./results**.

```bash
python test.py --mode single \
  --image your_pic_path \
  --checkpoint best_model_ema.pth \ 
  --save_dir ./results \
  --zoom 1.2 \
  --percentile_lo 1 \ 
  --percentile_hi 99 \
```

The **zoom** parameter controls the scaling factor for the lungs.

The **percentile_lo** and **percentile_hi** relate to contrast, and in most cases it is acceptable to retain the default values.



## 📧 Contact

If you have any questions, please feel free to email: yl2123@hw.ac.uk. We have plans to **expand the dataset and continue developing new features**. This repository will be **updated and maintained** going forward.
