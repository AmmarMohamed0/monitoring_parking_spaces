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
## get_spot
Imports:

- `cv2`: OpenCV library for computer vision tasks.
- `numpy`: Library for numerical computing.
- `pickle`: Library for serializing and deserializing Python objects.
- `cvzone`: A computer vision library built on top of OpenCV.

Variable Initialization:

- `drawing`: A boolean flag to track if the user is currently drawing an area.
- `areaName`: A list to store names of defined areas.
- `points`: A list to store the points defining the area being drawn.
- `current_name`: A variable to temporarily store the name of the current area being drawn.

Video Capture:

- Opens a video file named "ParkWatch.mp4" for processing using `cv2.VideoCapture`.

Loading Saved Area Information:

- Tries to load previously saved area information (polylines and area names) from a file named "points_and_names_of_area" using `pickle`.
- If the file is not found, initializes `polylines` as an empty list.

Function to Draw Area by Mouse:

- Defines a callback function `draw` to handle mouse events for drawing areas.
- On left button down event (`cv2.EVENT_LBUTTONDOWN`), starts recording points.
- On mouse move event (`cv2.EVENT_MOUSEMOVE`), records points while the left button is pressed.
- On left button up event (`cv2.EVENT_LBUTTONUP`), stops recording points, prompts the user for the name of the area, and appends the area name and its defining points to `areaName` and `polylines`, respectively.

Video Frame Processing Loop:

- Enters a loop to process each frame of the video.
- Resizes each frame to a fixed size.
- Draws previously defined areas (polylines) on the frame.
- Sets a mouse callback function (`draw`) to handle mouse events for defining new areas.
- Displays the frame with areas drawn (`cv2.imshow`).

Key Press Handling:

- Waits for a key press for a specified duration (60 milliseconds) using `cv2.waitKey`.
- If the 's' key is pressed, saves the defined areas and their names to a file named "points_and_names_of_area" using `pickle.dump` and exits the loop.
- If the 'q' key is pressed, exits the loop.

Releasing Resources:

- Releases the video capture object (`cap.release()`).
- Closes all OpenCV windows (`cv2.destroyAllWindows()`).

This code allows users to interactively define areas of interest within a video by drawing polygons using the mouse. It provides functionality to save the defined areas along with their names for future use.
