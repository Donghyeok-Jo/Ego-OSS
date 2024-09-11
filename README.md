# Ego-OSS
This is the dataset recipe from the paper "Egocentric On-screen Sound Source Separation for Real-time Edge Computing".
Demos of Ego-OSS can be found at this link. [(https://donghyeok-jo.github.io/Ego-OSS)](https://donghyeok-jo.github.io/Ego-OSS)


## overview
Since there are no publicly available datasets for egocentric OSS, we propose a new audio-visual dataset for this task by combining public datasets. Given the self-supervised structure of our method, it is possible to use datasets from other tasks without labels. We follow the mix-and-separate framework, constructing on-screen data with an audio-visual video dataset and combining off-screen noise with an audio-only dataset.


## On-screen Egocentric Video Dataset
As the on-screen data, we use [EPIC-KITCHENS](https://epic-kitchens.github.io), a large egocentric dataset. The dataset consists of 100 hours of egocentric recordings from 45 kitchen scenes.

### Preparation
1. Download videos.

    1) Download Epic-Kitchens dataset using [epic_downloader](https://github.com/epic-kitchens/epic-kitchens-download-scripts).

2. Preprocess videos. 

    1) Trim the video using the official annotations, for example, the test video timestamps can be found at https://github.com/epic-kitchens/epic-kitchens-100-annotations/blob/master/EPIC_100_test_timestamps.csv.

	2) Select the clips that are longer than 3 seconds among the trimmed clips. 
    
    3) Extract waveforms at 11,050 Hz and resample video frames to 8 fps for all the clips.

	4) Follow the official train/test split

## Off-screen Audio-only Dataset
As the off-screen noise data, we use ESC-50\cite{b43} dataset. The dataset consists of 5-second-long recordings organized into 50 semantical classes (with 40 examples per class) loosely arranged into 5 major categories.

### Preparation
1. Download audios.

	1) Download ESC-50 dataset at [here](https://github.com/karolpiczak/ESC-50)
	
2. Preprocess

	1) Resample all of audios to 11,050 Hz
	
	2) Split the dataset according to official 5-fold arrangement, using folds 1 through 4 as the training data and fold 5 as the test data.
	
## 