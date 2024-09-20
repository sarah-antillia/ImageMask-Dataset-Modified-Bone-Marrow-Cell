<h2>ImageMask-Dataset-Modified-Bone-Marrow-Cell (2024/09/20)</h2>

This is ImageMask Dataset for Modified-Bone-Marrow (MBM) Cell.<br>
The dataset used here has been taken from the github repository: 
<a href="https://github.com/ieee8023/countception/blob/master/MBM_data.zip">
MBM_data.zip
</a>
<br><br>
<b>Download ImageMask-Dataset</b><br>
You can download our dataset from the google drive 
<a href="https://drive.google.com/file/d/1_1DuF9idDVu45f8D-CJuWFWckuADzQ-6/view?usp=sharing">
MBM-ImageMask-Dataset-V2.zip</a>
<br>

<h3>1. Dataset Citation</h3>
We used the following MBM_dataset to create our ImageMask Dataset:<br>

<a href="https://github.com/ieee8023/countception/blob/master/MBM_data.zip">
https://github.com/ieee8023/countception/blob/master/MBM_data.zip</a><br>
<br>

Count-Ception: Counting by Fully Convolutional Redundant Counting (arXiv)
Joseph Paul Cohen, Genevieve Boucher, Craig A. Glastonbury, Henry Z. Lo, Yoshua Bengio

<a href="https://github.com/ieee8023/countception">https://github.com/ieee8023/countception</a>
<br>
<b>Citation request:</b><br>
Count-ception: Counting by Fully Convolutional Redundant Counting<br>
JP Cohen, G Boucher, CA Glastonbury, HZ Lo, Y Bengio<br>
International Conference on Computer Vision (ICCV) Workshop on Bioimage Computing<br>

@inproceedings{Cohen2017,<br>
title = {Count-ception: Counting by Fully Convolutional Redundant Counting},<br>
author = {Cohen, Joseph Paul and Boucher, Genevieve and Glastonbury, Craig A. and Lo, Henry Z. and Bengio, Yoshua},<br>
booktitle = {International Conference on Computer Vision Workshop on BioImage Computing},<br>
url = {http://arxiv.org/abs/1703.08710},<br>
year = {2017}<br>
}<br>


<h3>2. ImageMaskDataset Generation</h3>
Please download the master MBM dataset from 
<a href="https://github.com/ieee8023/countception/blob/master/MBM_data.zip">
MBM_data.zip</a>, and expand it in your working directory.
It contains 44 image and 44 dots files of 600x600 pixels.<br><br>
<img src="./asset/MBM_data.png" width="1024" height="auto"><br>
<br>
Enlarged image and dots files. 
As shown below, the dots file contains center points of the cell nuclei, not an ordinary segmentation mask file. <br>
<table>
<tr>
<th>image file </th>
<th>dots file </th>

</tr>
<tr>
<td><img src="./asset/BM_GRAZ_HE_0001_01_000.png" width="400" height="auto"> </td>
<td><img src="./asset/BM_GRAZ_HE_0001_01_dots_000.png" width="400" height="auto"> </td>

</tr>
</table>
<br>
Please run the following command for Python <a href="./ImageMaskDatasetGenerator.py">ImageMaskDatasetGenerator.py</a> 
<br>
<pre>
>python ImageMaskDatasetGenerator.py
</pre>
This generates 640x640 pixels image files, and segmentation mask files by drawing filled circles with a fixed radius around 
center points of the cell nuclei in the dots files,
<br>
This creates an augmented MBM-master-V2 dataset from MBM_data by using the offline augmentation tool ImageMaskDatasetGenerator.py.<br>
<pre>
./MBM-master-V2
├─images
└─masks
</pre>
<table>
<tr>
<th>image file </th>
<th>mask file </th>

</tr>
<tr>
<td><img src="./asset/BM_GRAZ_HE_0001_01_000.png" width="400" height="auto"> </td>
<td><img src="./asset/1001.jpg" width="400" height="auto"> </td>

</tr>
</table>

 
<h3>3. Split master</h3>

Please run the following command for Python <a href="./split_master.py">split_master.py</a> 
<br>
<pre>
>python split_master.py
</pre>
This creates MBM-ImageMask-Dataset-V2 from MBM-master-V2.<br>
<pre>
./MBM-ImageMask-Dataset-V2
├─test
│  ├─images
│  └─masks
├─train
│  ├─images
│  └─masks
└─valid
    ├─images
    └─masks
</pre>
<hr>
<b>Train images sample</b><br>
<img src="./asset/train_images_sample.png" width=1024 heigh="auto"><br><br>
<b>Train mask sample</b><br>
<img src="./asset/train_masks_sample.png" width=1024 heigh="auto"><br><br>


<b>Dataset Statistics</b> <br>
<img src="./MBM-ImageMask-Dataset-V2_Statistics.png" width="512" height="auto"><br>
