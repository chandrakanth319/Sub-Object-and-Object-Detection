Title: Object and Sub-object Detection Using YOLOv8
This project focuses on developing a system that performs real-time object and sub-object detection using the YOLOv8 framework. The system processes frames from a video, detects objects in each frame, identifies sub-objects within the detected objects, and outputs the results in a structured JSON format. The objective is to evaluate the system’s performance, particularly its ability to perform these tasks in real time, while maintaining a balance between speed and accuracy.

The implementation uses two YOLOv8 models: one as the main model for detecting primary objects and the other as a sub-model for detecting objects within the cropped regions corresponding to the main detections. The video frames are processed sequentially. Each frame undergoes a series of steps where objects are detected, their bounding boxes are extracted, and sub-object detection is performed on the cropped regions. This hierarchical approach ensures that the results can be comprehensively represented in a nested JSON structure, where each main object includes details about its associated sub-objects.

The system’s architecture was designed with efficiency in mind. YOLOv8n, the nano version of YOLOv8, was chosen for both the main and sub-models due to its lightweight nature and speed, making it suitable for real-time applications. OpenCV was used for video processing, which allowed frame-by-frame extraction and manipulation, while the structured JSON output was handled using Python’s built-in json module.

The performance of the system was benchmarked on a hardware configuration consisting of an Intel Core i5 processor, NVIDIA RTX 3070 GPU, and 32GB of RAM. The test video, "Chandu.mp4," had a resolution of 1920x1080 and a frame rate of 30 FPS. The system processed 300 frames in approximately 11.72 seconds, resulting in an average processing speed of 25.6 frames per second (FPS). This speed indicates that the system can handle real-time video feeds effectively, provided the hardware supports GPU acceleration.

During the evaluation, the system demonstrated its ability to detect main objects and sub-objects with reasonable accuracy. However, it was noted that the sub-object detection step introduced a slight overhead due to the additional inference required on cropped regions. This overhead, while noticeable, did not significantly hinder the real-time capabilities of the system, as the processing speed remained above the typical threshold of 24 FPS required for smooth video playback.

To optimize the performance, several strategies were implemented. First, lightweight YOLOv8n models were used, which are specifically designed for scenarios where speed is a priority. Second, cropped regions for sub-object detection were restricted to the bounding boxes of the main detections, thereby reducing unnecessary computations. Finally, GPU acceleration was leveraged to handle the computational load efficiently.

Despite the system's success, certain challenges were encountered. The inference speed was impacted when processing high-resolution frames, particularly when multiple objects were detected in a single frame, leading to a larger number of cropped regions for sub-object detection. Additionally, the reliance on sequential frame processing, while simpler to implement, limits the scalability of the system when handling multiple video feeds simultaneously.

In conclusion, the project demonstrates that a hierarchical detection system using YOLOv8 can achieve real-time performance while producing structured outputs suitable for downstream applications. The system's ability to detect and organize objects in a nested format provides a robust solution for use cases like automated video analysis, surveillance, and object tracking. However, further optimizations, such as implementing parallel processing and exploring dynamic cropping strategies, could enhance both the speed and scalability of the system.























