# Pose Guided Human Image Generation with Deformable GANs and Human Joint Pairs

![img1](https://user-images.githubusercontent.com/58557243/71240437-783d6e80-234c-11ea-9ad6-d635b40e554a.PNG)

## Reference
- [pose-gan](https://github.com/AliaksandrSiarohin/pose-gan)
- Referenced github repository. Thank you.

## Prepare Data
- DownLoad Market Dataset
  - [Market Dataset](https://drive.google.com/file/d/0B8-rUzbwVRk0c054eEozWG9COHM/view)
- DownLoad Fasion Dataset
  - [DeepFasion Dataset](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion/InShopRetrieval.html)
  - Data Tree
  ```
  ├── data
    ├── market-dataset
    |  ├── gt_bbox
    |  ├── gt_query
    |  ├── query
    |  ├── bounding_box_test -> test
    |  ├── bounding_box_train -> train  
    |  └── readme
    └── fasion
       ├── MEN
       └── WOMEN
  ```

## Training
1. We need to divide the train dataset and test dataset from the whole fasion dataset.
```
python split_fasion_dataset.py
```
2. training FULL(JointPair + DCSU) model
```
python train.py --output_dir output/full_stickhm_conv_train_market --checkpoints_dir output/full_stickhm_conv_train_market --pose_rep_type stickhm --warp_skip conv --dataset market --l1_penalty_weight 0.01 --nn_loss_area_size 3 --batch_size 4 --content_loss_layer block1_conv2 --number_of_epochs 90
```

## Testing


## Requirements
- python == 3.5
- cuda == 9.0
- tensorflow-gpu == 1.8.0
- keras == 2.1.5
- keras_contrib
  ```
  git clone https://github.com/keras-team/keras-contrib.git
  cd keras-contrib
  python setup.py install
  ```
