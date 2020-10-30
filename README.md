# IMUTube
Hyeokhyen Kwon, Catherine Tong, Harish Haresamudram, Yan Gao, Gregory D. Abowd, Nicholas D. Lane, and Thomas Plötz. 2020. \
IMUTube: Automatic Extraction of Virtual on-body Accelerometry from Video for Human Activity Recognition. \
Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. 4, 3, Article 87 (September 2020), 29 pages. \
DOI:https://doi.org/10.1145/3411841

## Dataset
### Locomotion activities
The video sources are from [RealWorld (HAR)](https://sensor.informatik.uni-mannheim.de/#dataset_realworld), which include 15 Subjects and 8 activity classes.\
We segmented each downloaded video into 2-minutes clips, and then IMUTube pipeline is run on each clip. The videos are commonly 10 minutes long, so that around 5 clips exist for each activity video. (Please check the details from the original dataset page.)\
Each sample directory name is {subject_ID}\_{activity_class}\_{clip_number}.\
Also, each clip can output multiple person, which are identified with its pID (person ID), even when a single person exists in the video. The IMUTube pipeline considers the detected person in the next frame is a new person if SORT tracking algorithm fails to track the person, and assigns a new ID.\
The following downloaded dataset includes resulting outputs from IMUTube pipelin:
1. 3D motion estimation for each pID ([bvh file](http://www.cs.man.ac.uk/~toby/bvh/))\
If you want to get 3D pose estimation without global motion estimation, set HIP translation and rotation to zeros. \
We observed that global motion estimation can be erroneous depending on the complexity of the scene, whereas pose estimation is relatively stable.\
Before extracting virtual IMU data, you can freely change the scale of each bone of the 3D character to represent the activities from different types of people.
2. Estimated frame numbers in video for each pID (python 3.X pickle file) \
Remember that each clips are 2 minutes length segmentations from original 10 minutes video. Make sure to count from its correct starting time.\
The pickle file is dictionary with pID as key and frame number list as item. ({pID:[0,1,2,...]})
3. Accelerometer and Gyroscope data for each sensor location for each pID ([npz file](https://numpy.org/doc/stable/reference/generated/numpy.load.html))

[Download](https://www.dropbox.com/s/orufwrnlncezbh1/locomotion.tar.gz?dl=0)

### Complex activities
The complex activity video sources are from multiple video benchmark datasets (Please, refer the citations in paper).\
Each sample directory name is {benchmark_dataset_source}\_{activity_class}\_{YouTube_video_ID}\_{start_timestep}\_{end_timestep}. Each information comes from original benchmark dataset.\
The following downloaded dataset includes the same content as explained in locomotion activity.

[Download]()
