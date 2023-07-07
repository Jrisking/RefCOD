# <p align=center>`Referring Camouflaged Object Detection `</p>
This official repository contains the dataset, source code of paper 'Referring Camouflaged Object Detection'.   
In this paper, we consider the problem of referring camouflaged object detection (RefCOD), a new task that aims to segment specified
camouflaged objects based on a small set of referring images with salient target objects. 
  
**1. Method.**
<p align="center">
    <img src="figs/r2cnet.png" width="950"/> <br />
</p>

&emsp; Our R2CNet framework is composed of two branches, i.e., reference branch in green and segmentation branch
in orange. In the reference branch, the common representation of a specified object from images is obtained by masking and pooling the visual
features with the foreground map generated by a SOD network. In the segmentation branch, the visual features from the last three layers of the
encoder are employed to represent the given image. Then, these two kinds of feature representations are fused and compared in the well-designed
RMG module to generate a mask prior, which is used to enrich the visual feature among different scales to highlight the camouflaged targets in our
RFE module. Finally, the enriched features are fed into the decoder to generate the final segmentation map. DSF:Dual-source Information Fusion, MSF: Multi-scale Feature Fusion, TM: Target Matching.

**2. Datasets.**

- To reproduce our results, you should first download our ensembled [R2C7K](https://pan.baidu.com/s/1Tcvt0IJYdKSYAb_BD5QrTg?pwd=2gf4) dataset with access code ```2023``` on Baidu Netdisk.
- Update the 'data_root' param with your R2C7K location in train.py and test.py.

**3. Test.**
- Download our pre-trained [R2CNet]() checkpoints with access code 2023 on Baidu Netdisk.
- Put the checkpoint file on './snapshot/saved_models/'.
- Run ```python test.py``` to evaluate the performance of R2CNet.
