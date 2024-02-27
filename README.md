# monitoring_parking_spaces
## Imports:

- `cv2`: OpenCV library for computer vision tasks.
- `numpy`: Library for numerical computing.
- `pickle`: Library for serializing and deserializing Python objects.
- `pandas`: Library for data manipulation and analysis.
- `ultralytics.YOLO`: YOLO (You Only Look Once) object detection model from Ultralytics.
- `cvzone`: A computer vision library built on top of OpenCV.

Reading Class Names:

- Reads class names from a file named "coco.txt" and stores them in a list.

Loading YOLO Model:

- Initializes a YOLO model using the yolov8s.pt weights file.

Loading Area Information:

- Loads predefined area information (polylines and area names) from a file using pickle.

Opening Video Capture:

- Opens a video file named "ParkWatch.mp4" for processing.

Processing Video Frames:

- Enters a loop to process each frame of the video.
- Resizes each frame to a fixed size.
- Uses the YOLO model to detect objects (cars) in the frame.
- Extracts bounding box coordinates and class information of detected cars.
- Calculates the center coordinates of detected cars.
- Checks if the detected object is a car and stores its center coordinates.

Analyzing Parking Spaces:

- Draws polylines representing parking areas on the frame.
- Checks if the center coordinates of each car lie within any of the predefined parking areas.
- Updates the visualization to indicate occupied (red) and unoccupied (green) parking spaces.
- Calculates and displays the number of occupied and free parking spots.

Displaying Results:

- Displays the processed frame with parking space occupancy information.
- Waits for a key press (60 milliseconds) to process the next frame.
- If the 'q' key is pressed, breaks out of the loop.

Releasing Resources:

- Releases the video capture object.
- Closes all OpenCV windows.

This code essentially performs real-time monitoring of parking spaces in a video feed, providing visual feedback on the occupancy status of each parking spot. It uses YOLO for object detection and OpenCV for video processing and visualization.
