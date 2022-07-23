# IMUTube
Hyeokhyen Kwon, Catherine Tong, Harish Haresamudram, Yan Gao, Gregory D. Abowd, Nicholas D. Lane, and Thomas Plötz. 2020. \
IMUTube: Automatic Extraction of Virtual on-body Accelerometry from Video for Human Activity Recognition. \
Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. 4, 3, Article 87 (September 2020), 29 pages. \
DOI:https://doi.org/10.1145/3411841

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/ZN41C_fOdmk/1.jpg)](https://www.youtube.com/watch?v=ZN41C_fOdmk)

Hyeokhyen Kwon, Bingyao Wang, Gregory D. Abowd, and Thomas Plötz. 2021. \
Approaching the Real-World: Supporting Activity Recognition Training with Virtual IMU Data. \
Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. 5, 3, Article 111 (Sept 2021), 32 pages. \
DOI:https://doi.org/10.1145/3478096

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/cajum1dbRQY/2.jpg)](https://youtu.be/cajum1dbRQY)

Kwon, Hyeokhyen, Gregory D. Abowd, and Thomas Plötz. 2021. \
"Complex Deep Neural Networks from Large Scale Virtual IMU Data for Effective Human Activity Recognition Using Wearables" \
Sensors 21, no. 24: 8337. \
https://doi.org/10.3390/s21248337

## Softward Licensing

For the source code of this project, please consult Georgia Tech License office! \
They normally license techonology to other universities for free for internal R&D only. \
Please check [here](https://licensing.research.gatech.edu/technology/imutube-converting-videos-human-activity-virtual-imu-data-streams)!

## Dataset
### Locomotion activities
The video sources are from [RealWorld (HAR)](https://sensor.informatik.uni-mannheim.de/#dataset_realworld), which include 15 Subjects and eight activity classes.\
We segmented each downloaded video into 2-minutes clips, and then the IMUTube pipeline is run on each clip. The videos are commonly 10 minutes long so that around five clips exist for each activity video. (Please check the details from the original dataset page.)\
Each sample directory name is {subject_ID_from_original_dataset}\_{activity_class}\_{clip_number}. \
Also, each clip can output multiple persons identified with its pID (person ID), even when a single person exists in the video. The IMUTube pipeline considers the detected person in the next frame as a new person if the [SORT](https://github.com/abewley/sort) tracking algorithm fails to track the person and assigns a unique ID or when [scene boundary](https://github.com/Tangshitao/ClipShots_basline) is detected.\
There are also a few video clip samples that were failed to generate virtual IMU samples.\
The following downloaded dataset includes resulting outputs from the IMUTube pipeline:
1. 3D motion estimation for each pID ([bvh file](http://www.cs.man.ac.uk/~toby/bvh/))\
If you want to get 3D pose estimation without global motion estimation, set HIP translation and rotation to zeros. \
We observed that global motion estimation could be erroneous depending on the complexity of the scene, whereas pose estimation is relatively stable.\
Before extracting virtual IMU data, you can freely change the scale of each bone of the 3D character to represent the activities of different types of people.
2. Estimated frame numbers in a video for each pID (python 3.X pickle file) \
Remember that each clip is 2 minutes length segmentations from the original 10 minutes video. Make sure to count from its correct starting time.\
A pickle file is a dictionary with pID as a key and frame number list as an item. ({pID:[0,1,2,...]})
3. Accelerometer and Gyroscope data for each sensor location for each pID ([npz file](https://numpy.org/doc/stable/reference/generated/numpy.load.html))\
The npz file includes the numpy array of sensor stream for each sensor location ({sensor_name:np.array}).

[Download](https://www.dropbox.com/s/orufwrnlncezbh1/locomotion.tar.gz?dl=0)

### Complex activities
The complex activity classes include 'cycling', 'folding_laundry', 'ironing', 'rope_jumping', 'soccer', 'vacuum_cleaning'.\
The complex activity video sources are from multiple video benchmark datasets (Please, refer to the citations in the paper).\
For the benchmark dataset that provides link to Youtube and the activity segment (ActivityNet or Kinetics), each sample directory name is {benchmark_dataset_source}\_{activity_class_from_bechmark_dataset}\_{YouTube_video_ID}\_{start_timestep}\_{end_timestep}.\
If the benchmark dataset provides video samples directly (hmdb51, mpiim, ucf101, and etc.), each sample directory name is {benchmark_dataset_source}\_{activity_class_from_bechmark_dataset}\_{video_ID_from_benchmark_dataset}.
Please, refer to each benchmark dataset for the details. Each information comes from the original benchmark dataset.\
The following downloaded dataset includes the same content as explained in locomotion activity.\
Additionally, the dataset includes the virtual IMU data for [Pamap2](https://archive.ics.uci.edu/ml/datasets/PAMAP2+Physical+Activity+Monitoring) dataset and [RealWorld (HAR)](https://sensor.informatik.uni-mannheim.de/#dataset_realworld).

[Download](https://www.dropbox.com/s/t87pjaignz0gamo/complex.tar.gz?dl=0)

### Gym Exercise 

The two datasets include videos queried from youtube for 13 dumbbell activities in the experiment. \
One datset is used for supervised learning with manually annotated exercise segment. \
The other dataset is used for weakly supervised learning by using the search query keyword as target label. 

Labeled Dataset \
[Video Links](https://www.dropbox.com/s/i0yj4weucgnhsv6/annotated_video.json?dl=0) 

UnLabeled Dataset \
[Video Links](https://www.dropbox.com/s/kbg9d2tm3s8ibil/weakly_labeled_video.json?dl=0) \
[Sensor Links](https://www.dropbox.com/s/q6ftesrgjwdz6af/weak.npz?dl=0)

Labels: \
0: 'One-Arm Dumbbell Row', \
1: 'Incline Dumbbell Flyes', \
2: 'Incline Dumbbell Press', \
3: 'Dumbbell Flyes', \
4: 'Tricep Dumbbell Kickback', \
5: 'Dumbbell Alternate Bicep Curl', \
6: 'Incline Hammer Curl', \
7: 'Concentration Curl', \
8: 'Hammer Curl', \
9: 'Side Lateral Raise', \
10: 'Front Dumbbell Raise', \
11: 'Seated Dumbbell Shoulder Press', \
12: 'Lying Rear Delt Raise'
