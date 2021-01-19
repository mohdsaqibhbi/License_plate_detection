# License_plate_detection
This repo is about training a model that can detect the license plate, using an object detection algorithm Yolo v3.

## How to run
- Clone the repo using `git clone https://github.com/mohdsaqibhbi/License_plate_detection`.
- Go to this directory using `cd License_plate_detection`
- Create virtual environment.
- Install dependencies using `pip install -r requirements.txt`.
- Put train images in directory `data/train/images/` and validation images in directory `data/val/images`.
- Put train labels in directory `data/train/labels/` and validation labels in directory `data/val/labels`.
- Create `license_plate.yaml` file.
    `# train and val data as 1) directory: path/images/, 2) file: path/images.txt, or 3) list: [path1/images/, path2/images/]
    train: data/license_plate/train/images/
    val: data/license_plate/val/images/

    # number of classes
    nc: 1

    # class names
    names: ['license_plate']`
    
- Download the pretrained weights using `bash weights/download_weights.sh` and put them in the directory `data/pretrained/`.
- Train the model using 
  `python train.py --img 608 --batch 16 --epochs 1000 --data data/license_plate.yaml --weights data/pretrained/yolov3.pt --nosave --cache --project data/output --name ''`
- Detection
  `python detect.py --weights data/output/weights/last.pt --img 608 --conf 0.5 --source data/test/test.jpg --project data/detect --name ''`
  **Before detection**
  ![](test/img2.jpg)
  **After detection**
  ![](detect/img2.jpg)
  **Cropped**
  ![](detect/roi_img2.jpg)
