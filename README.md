# Intelligent Facial Recognition 🪪 for Institutional Exam Attendance
This repository contains the implementation of my research titled _"Intelligent Facial Recognition for Institutional Exam Attendance"_ at the Department of Mechatronics Engineering (DOME), Federal University of Technology, Minna.

---

## 🧭 Overview
This study proposes a multi-facet facial recognition model based on the K-Nearest Neighbors (KNN) algorithm for recording and verifying student attendance during examination scenarios. The model was trained to operate under different conditions by leveraging 990 pre-registered students’ image data captured across multiple settings. The process involved face detection using a pre-trained Haar Cascade classifier, followed by face alignment and encoding into 128-dimensional vectors using a ResNet-based approach, which 
were then classified by the KNN algorithm. Evaluation across static images, video, and real-time camera feeds achieved an accuracy of over 99.00% with a response time of 6.00s seconds. Compared to traditional manual attendance systems, the proposed model provides an efficient solution for examination verification, effectively 
mitigating recognition challenges caused by varying environmental and facial conditions. 

---

## 🎯 Research Objectives

- To capture student facial data irrespective of subtle changes in facial appearance.
- To develop a facial recognition model capable of attendance authorizaton of examination students.
- To evaluate the model's performance in verifying student attendance authorization.

---

## ⚙️ Tools and Technologies Used

| **Tool / Library**                          | **Purpose in the Project**                                                                                                                  |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **OpenCV (cv2)**                            | Handled image capture, video processing, face detection (via Haar Cascade), drawing bounding boxes, and overlaying frames on the interface. |
| **os**                                      | Managed file paths, checked directory existence, accessed folders for datasets, and handled file creation.                                  |
| **numpy (np)**                              | Performed numerical operations and supported array manipulation needed in encoding and evaluation tasks.                                    |
| **Pillow (PIL)**                            | Provided additional image manipulation utilities during preprocessing.                                                                      |
| **face_recognition**                        | Detected faces, computed 128-dimensional face encodings, and provided core facial recognition functionality.                                |
| **pickle**                                  | Saved and loaded the trained KNN model and facial encodings for recognition and evaluation.                                                 |
| **scikit-learn (KNeighborsClassifier)**     | Implemented the K-Nearest Neighbors classifier used for facial recognition and prediction.                                                  |
| **glob**                                    | Located image file paths when loading training and testing datasets.                                                                        |
| **time**                                    | Measured timestamps and enabled timed delays, especially during attendance recording.                                                       |
| **csv**                                     | Read and wrote attendance records into CSV files with timestamps.                                                                           |
| **datetime**                                | Generated human-readable date and time formats for attendance entries.                                                                      |
| **win32com.client (Dispatch)**              | Enabled text-to-speech functionality for voice feedback (e.g., “Attendance Taken”).                                                         |
| **matplotlib.pyplot**                       | Created visualizations, especially confusion matrix heatmaps.                                                                               |
| **seaborn**                                 | Enhanced visualization aesthetics for plots such as heatmaps.                                                                               |
| **classification_report (sklearn.metrics)** | Provided precision, recall, and F1-score for evaluating model performance.                                                                  |
| **confusion_matrix (sklearn.metrics)**      | Computed confusion matrices used to assess correct and incorrect classification counts.                                                     |

## 📝 Step by Step Procedure


