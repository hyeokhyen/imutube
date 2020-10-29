# IMUTube
Hyeokhyen Kwon, Catherine Tong, Harish Haresamudram, Yan Gao, Gregory D. Abowd, Nicholas D. Lane, and Thomas Plötz. 2020. IMUTube: Automatic Extraction of Virtual on-body Accelerometry from Video for Human Activity Recognition. Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. 4, 3, Article 87 (September 2020), 29 pages. DOI:https://doi.org/10.1145/3411841

## Dataset
### Locomotion activities
The video sources are from [RealWorld (HAR)](https://sensor.informatik.uni-mannheim.de/#dataset_realworld), which include 15 Subjects and 8 activity classes.
We segmented each downloaded video into 2-minutes clips, and then IMUTube pipeline is run on each clip.
Also, each clip can output multiple person, which are identified with its pID (person ID), even when a single person exists in the video. The IMUTube pipeline considers the detected person in the next frame is a new person if SORT tracking algorithm fails to track the person, and assigns a new ID.
The following downloaded dataset includes resulting outputs from IMUTube pipelin:
1. 3D motion estimation for each pID (bvh file) ([BVH file format info and renderers](http://www.cs.man.ac.uk/~toby/bvh/))
2. Estimated frame numbers in video for each pID (python 3.X pickle file) 
Remember that each clips are 2 minutes length segmentations from original 10 minutes video. Make sure to count from its correct starting time.
The pickle file is dictionary with pID as key and frame number list as item.
3. Accelerometer and Gyroscope data for each sensor location for each pID (npz file)
[Download]()

### Complex activities
