# Droplet Detection using instance segmentation installation: 

1. Activate the Anaconda environment:
   conda activate yolov8_segmentation
 
2. Install "labelme" for annotation:
  pip install labelme

3. Annotate droplets using "labelme."

4. Convert annotated images to YOLO format:
    pip install labelme2yolo
    labelme2yolo --json_dir dataset/train

5. Update paths in "dataset.yaml" for training and validation folders.

6. Install "ultralytics":
pip install ultralytics

7. Train the YOLOv8 model:
yolo task=segment mode=train epochs=100 data=dataset.yaml model=yolov8m-seg.pt imgsz=640 batch=8
 
8. Rename "best.pt" to "yolov8m-seg-custom.pt" in the "Yolov8_Segmentation_Custom" folder.

9. Place sample image/video in "Yolov8_Segmentation_Custom."
 
10. Create a text file named "Predict.py" and enter the following code: 
from ultralytics import YOLO
model = YOLO("yolov8m-seg-custom.pt")
model.predict(source="1.png", show=True, save=True, hide_labels=False, hide_conf=False, conf=0.5, save_txt=False, save_crop=False, line_thickness=2)

11. Run the code:
   python Predict.py
