# Development of a Multi-facet Facial Recognition Model for Institutional Attendance Activities During Examination Scenario.

This repository contains the implementation of my research titled [_"Development of a multi-facet facial recognition model for institutional attendance activities 
during examination scenario"_](https://link.springer.com/article/10.1007/s44163-026-01474-y), published in the [_Discover Artificial Intelligence Journal_](https://link.springer.com/journal/44163) and authored by Jack, K.E., Rizama, V.S., Adebayo, K.R., Ambafi, J.G., Olayemi, R.A., Olaoye, J.O., Tunbosun, D.O., & Olawuyi, A.V. (2026).

---

## 🧭 Overview
This research proposes a multi-facet facial recognition model based on the K-Nearest Neighbors (KNN) algorithm for recording and verifying student attendance during examination scenarios. The model was trained on a dataset of 990 images to operate under different conditions by leveraging pre-registered students’ data captured across multiple settings. The process involved face detection using a pre-trained Haar Cascade classifier, followed by face alignment and encoding into 128-dimensional vectors using a ResNet-based approach, which 
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
| **CSI Camera Module**                       | Use for capturing and inputting the facial image data of the students. |
| **OpenCV**                            | Handled image capture, video processing, face detection (via Haar Cascade), drawing bounding boxes, and overlaying frames on the interface. |
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

---

## 📝 Methodology - Step by Step Implementation Procedure

 - **Data Collection:** Initially, a total of 34,064 facial images were collected from three students using the CSI camera module. Specifically, images were collected in:
   
    - Bright and dim light scenarios.
    - Different head positions ( specifically + or - 15 degrees to the left and right) **AND**
    - With the use of different accessories (specifically, with glasses and beards).
  

- **Preprocessing and preparation:** The data pre-processing step involved three stages namely:
   - **Image Resizing:** To ensure uniformity across the entire dataset and to meet the requirements of the multi-facet facial recognition model, each cropped face image was rescaled to a fixed size of 400 × 400 pixel using 
OpenCV’s `resize` function.
   - **Grayscale Conversion:** Following the image resizing step, the next pre-processing technique applied was gray scaling. This technique transformed the resized 400 x 400-pixel color images from the BGR color space captured by OpenCV to grayscale.
     
      **NOTE:** It was important to use grayscaled images:
      *   Because color was **NOT** a significant factor in determining the identity of a person.
      *   To reduce computational cost during the training in later stages.
  
   - **Class Balancing:** To ensure good performance of the multi-facet facial recognition model across different scenarios, the data preparation process involved reducing the initial dataset of 34, 064 images to 990 through a careful collection process. It further ensured that there was an equal distribution of 330 images across the three students in bright and dark lighting scenarios as well as different head positions and facial appearance after which the resulting dataset was used for the training process in the later stages.

- **Face detection:** Because facial data was the primary focus in building the model, a Haar Cascade classifier was used for face detection which involved processing each image frame captured by the camera, and detecting candidate face bounding boxes at multiple scales.

- **Cropping:** After the face detection, detected face regions were cropped from the original frame using the bounding box coordinates.

- **Face localization & landmark extraction:** This involved identifying face locations in each image by leveraging dlib's implementation of Histogram of Oriented Gradients (HOG) algorithm combined with a Support Vector Machine (SVM) classifier. 

- **Feature encoding:** Following the facel localization and landmark extraction procedure, a 128-dimensional vector for each detected face was generated by using a ResNet deep learning model architecture.

- **Model Training / classification:** The feature encoded vectors were then trained on a KNN algorithm which compared incoming embeddings to already stored embeddings to determine a match when similarity exceeded a threshold.

- **Attendance logging:** Recognized individuals were then recorded in an attendance file with their ID and timestamp.

- **Visualization:** OpenCV overlaid bounding boxes and labels on the displayed frames to show recognition results in real time. The procedure was then repeated for the next frame, enabling continuous, real-time attendance recognition.

---

## 🖼️ Results

### 📷 The Student Facial Capturing Results
**Note:** The difference in contrast, blur and brightness as seen in the collection of images below was taken ***intentionally*** to enable the model properly generalize to different lighting variations during real-time recognition.

<p align="center">
  <img src="recognition_results/facial_capturing_results.png" alt="facial_capturing_results" width="800" />
    <br>
    <em> A Collection of the Student Facial Capturing Results</em>
</p>

### 📷 The Real-time Recognition Results

<p align="center">
  <img src="recognition_results/real-time_recognition_results.png" alt="real-time_recognition_results" width="800" />
    <br>
    <em> A Collection of the Real-time Recognition Results </em>
</p>

### 📄 Results for the Model Evaluation on Images

| Student    | Test Images | Images Processed | Images Not Processed | Precision | Recall | F1-Score |
|------------|-------------|------------------|---------------------|-----------|--------|----------|
| Student 1  | 1000        | 629              | 371                 | 1.0000    | 1.0000 | 1.0000   |
| Student 2  | 1000        | 462              | 538                 | 1.0000    | 0.9978 | 0.9989   |
| Student 3  | 1000        | 659              | 341                 | 0.9984    | 1.0000 | 0.9992   |

### 📄 Results for the Model Evaluation on Video

| Student    | Total Test Video Frames | Frames Processed | Frames Not Processed | Precision | Recall | F1-Score |
|------------|-------------------------|------------------|----------------------|-----------|--------|----------|
| Student 1  | 1544                    | 1215             | 329                  | 0.9959    | 0.9934 | 0.9946   |
| Student 2  | 699                     | 492              | 207                  | 0.9979    | 0.9593 | 0.9782   |
| Student 3  | 2930                    | 2352             | 578                  | 0.9903    | 0.9996 | 0.9949   |

### 📄 Confusion Matrix Results 

<p align="center">
    <img src="recognition_results/confusion_matrix_image.png" alt="confusion_matrix_image" width="800"/>
    <br>
    <em> The Confusion Matrix for the Evaluation on Images</em>
</p>

<p align="center">
    <img src="recognition_results/confusion_matrix_video.png" alt="confusion_matrix_video" width="800"/>
    <br>
    <em> The Confusion Matrix for the Evaluation on Videos</em>
</p>

### Real-time Evaluation

Real-time performance of the multi-facet facial recognition model was evaluated under three key conditions: lighting variations, head positions, and appearance changes using two primary metrics namely **False Omission Rate (FOR)** and **response time**. For each of the three students, the FOR was measured across three head orientations (straight, `15°` right tilt, and `15°` left tilt), tested both with and without glasses under bright and dim lighting. Across all scenarios, each student completed six genuine recognition attempts, and the model recorded **no missed identifications**, resulting in a **0% False Omission Rate (FOR)**.

For the response time, the model demonstrated strong adaptability across all lighting and appearance conditions. Under bright lighting, it achieved an average response time of `4.02` seconds, reflecting efficient recognition in optimal conditions. In dim lighting, the average increased to `7.98` seconds due to reduced facial clarity, yet still confirmed the model’s capability to function reliably in low-light examination environments.

Appearance variations also affected performance: students wearing glasses or beards recorded an average response time of `6.21` seconds, compared to `5.79` seconds without accessories indicating only a modest increase in computation time. Head position tests revealed similar trends, with straight faces averaging `4.33` seconds, while `15°` leftward and rightward tilts produced `7.27` seconds and `6.40` seconds respectively, due to slight distortions in facial alignment.

Overall, the model achieved a mean response time of `6.00` seconds across all evaluated conditions, demonstrating its reliability for real-time recognition.

---

## 💡 Key Insights

- The use of  128-dimensional facial embeddings generated via a ResNet model was key in enabling effective differentiation between individuals even under challenging environmental and facial conditions.
- Observations on the evaluation metrics and confusion matrix for the images and videos showed that the model performed slightly better on images than on videos, consistently achieving near-perfect metrics for all students.
- The confusion matrices demonstrated strong classification capability, while the False Omission Rate (FOR) of 0% highlighted the model’s reliability in correctly identifying enrolled students.
- Real-time evaluation of the model's performance suggested high lighting tolerance, pose adaptability, and accessory robustness, supporting its suitability for real-time examination attendance monitoring.
- The overall average response time of 6.00 seconds across bright and dim conditions indicated the influence of lighting but reaffirmed the model’s efficiency for continuous operation.

## ✨ Research Novelty

The novelty and contribution of this research to knowledge was in the successful _**development and training of a multi-facet facial recognition model that recognized pre-registered students under different real-time conditions, specifically in varying lighting, head variations, and the use of accessories,  (limited to glasses and beards )**_. In contrast to conventional models, which often exhibited reduced performance under these conditions, this research improved the domain of intelligent educational attendance systems by providing a model that could be used for practical deployments in educational institutions. 

---

## 🔮Future Work

- Future improvements should address the challenge of distinguishing look-alike individuals (e.g., identical twins) through the creation of specialized impostor datasets for more rigorous testing.

- Although the current 128-dimensional embeddings provided strong discriminative power, expanding the dataset to include extreme lighting, wider head tilts, and additional accessories would further enhance robustness.

- Additional advancements could include integrating liveness detection to prevent spoofing, adopting advanced deep learning models such as CNNs or Transformers, and incorporating incremental learning to boost scalability and performance for larger examination cohorts.

---

## ⚠️ Disclaimer

The scope of this research focused on training the facial recognition model using a dataset lmited to three pre-registered students. As a result, the model could only verify the attendance of these three individuals and was evaluated according to its ability to recognize them under challenging conditions, including dark and dim lighting, changes in appearance such as the presence or absence of beards and glasses, and variations in head position and orientation.

---

## 📌 Note
Please kindly note that this README file is a summarized version of the full documentation of this research. The complete documentation, dataset and model weights can be provided upon request while the program implementation can be accessed via the [program script](KNN_Model_Development_For_Facial_Recognition.ipynb). 

---

## 👥 Contributors

- **Engr. Dr Kufre Esenowo Jack** : Supervisor
- **Rizama Victor Samuel**  [GitHub: Rizama-Victor](https://github.com/Rizama-Victor)
- **Adebayo Kehinde Rahmon**  
- **Rufai Ahmad Olayemi**  

---


