# LLM-Assisted Multi-Teacher Continual Learning for Visual Question Answering in Robotic Surgery

## Introduction
* The Pytorch implementation for our paper '[LLM-Assisted Multi-Teacher Continual Learning for Visual Question Answering in Robotic Surgery](https://arxiv.org/abs/xxxx.xxxxx)', submitted to ICRA 2024.

<p align="center">
  <img src="Figure/system.png"  width="1000"/>
</p>

## Data Preparation
* We use the dataset [EndoVis17](https://arxiv.org/abs/2305.11692), [EndoVis18](https://arxiv.org/abs/2206.11053), and [DAISI-VQA](DAISI_VQA). Note that DAISI-VQA is a new VQA dataset we build upon  [DAISI](https://arxiv.org/abs/2004.02809)

* How we constructed the DAISI-VQA dataset:

  The original DAISI dataset contains images and instructional texts of various surgical procedures on different organs. Each procedure consists of multiple images with corresponding instructional texts. We first clean the original DAISI dataset by deleting irrelevant images and confusing descriptions. We then generate QA pairs according to the text description for each image. Eventually, we obtained a new VQA dataset referred to as DAISI-VQA. Please see our paper for details about using in-context learning (ICL) for QA pair generation.

* Training and test data split

   EndoVis17: a VQA dataset obtained from 5 surgical videos. We use 73 frames (with 376 QA pairs) in the training set and 24 frames (with 96 QA pairs) in the  testing set.
  
   EndoVis18: a VQA dataset obtained from 14 surgical videos. We use 1560 frames (with 376 9014 pairs) in the training set and 447 frames (with 2769 QA pairs) in the testing set.
  
   DAISI-VQA: in total 346 surgical images and 469 QA pairs in the dataset. 80% of the data is used in the training set, while the rest 20% is used in the testing set.

## Environment & Setup
* See the “Environment and Preparation” section of our [Tutorial in Jupyter Notebook](code).
  
## Training
* We train the model under a continual learning (CL) framework.

* In time slot #1, we train the model with EndoVis17 dataset. Since our paper focuses on continual learning, we do need to repeat the conventional training process every time. So a fixed checkpoint for time slot #1 is given in our checkpoint folder. You can just just load the checkpoint to skip the training in time slot #1.

* Then in time slot #2, we train the model with EndoVis18 dataset.

* Finally, in time slot #3, we train the model with DAISI-VQA dataset.

* For details about the training process in time slots #1 and #2, please see our tutorial [here](code).; For details about the training process in time slot #3, please see our tutorial [here](code)..

## Testing
* After the training in time slot #1, we test the model on EndoVis17.

* After the training in time slot #2, we test the model on EndoVis17 and EndoVis18 to see if the new model forgets the knowledge in EndoVis17.

* After the training in time slot #3, we test the model on EndoVis17 EndoVis18, and DAISI-VQA to see if the new model forgets the knowledge in EndoVis17 and EndoVis18.

* For details about the testing  process in time slots #1 and #2, please see our tutorial [here](code).; For details about the testing process in time slot #3, please see our tutorial [here](code).

## Citation
If this repository is useful for your research, please cite:
```
@ARTICLE{xxx,  
  author={xxx},  
  journal={xxx},   
  title={LLM-Assisted Multi-Teacher Continual Learning for Visual Question Answering in Robotic Surgery},
  year={2023},  
  volume={xx},  
  number={x},  
  pages={xxxx-xxxx},  
  doi={xxx}
}
```
### Questions
For further questions about the code or paper, please contact 'kexinchen0526@gmail.com'
