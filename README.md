# **VR_Assignment1 - Coin Detection & Image Stitching**  
**Author:** Siddeshwar Kagatikar (IMT2022026)  

## **Overview**  
This repository contains two main tasks:  

1. **Coin Detection & Segmentation** - Detects and segments coins from input images.  
2. **Image Stitching (Panorama Creation)** - Stitches overlapping images into a seamless panorama.  

---

## **1️⃣ How to Run the Code**  

### **Step 1: Install Dependencies**  
Make sure you have Python installed, then install the required dependencies using:  
```bash
pip install -r requirements.txt
```

### **Step 2: Run Coin Detection & Segmentation**  
Navigate to the `Part1/` folder and run:  
```bash
jupyter notebook VR1.ipynb
```
or execute directly via:  
```bash
python Part1/src/main.py
```

### **Step 3: Run Image Stitching**  
Navigate to the `Part2/` folder and run:  
```bash
jupyter notebook VR2.ipynb
```
or execute via:  
```bash
python Part2/src/main.py
```

---

## **Repository Structure**
```
VR_Assignment1_SiddeshwarKagatikar_IMT2022026/
│── Part1/                 # Coin Detection & Segmentation
│   ├── input_coins/       # Input images (coins)
│   ├── contours/          # Contour-detected images
│   ├── Edges/             # Edge-detected images
│   ├── segments/          # Segmented coins of each image
│   │   ├── coin1/
│   │   ├── coin2/
│   │   ├── coin3/
│   │   ├── coin4/
│   ├── VR1.ipynb          # Jupyter Notebook for Part1
│
│── Part2/                 # Image Stitching (Panorama Creation)
│   ├── images/            # Input images (overlapping scenes)
│   ├── output/            # Stitched outputs
|   |   ├── keypoints_1_2.png
|   |   ├── keypoints_2_3.png 
│   │   ├── stitchedOutput.png
│   │   ├── stitchedOutputProcessed.png
│   ├── VR2.ipynb          # Jupyter Notebook for Part2
│
│── requirements.txt       # Dependencies
│── link.txt               # GitHub Link
│── README.md              # README file

```

---


## **2️⃣ Methods Used**  

### **🟡 Task 1: Coin Detection & Segmentation**  
- **Preprocessing**: Convert images to grayscale, apply Gaussian Blur.  
- **Edge Detection**: Use Canny Edge Detector for boundary identification.  
- **Contour Detection**: Extract contours of individual coins.  
- **Segmentation**: Crops and saves detected coins as separate images.  

### **🔵 Task 2: Image Stitching (Panorama Creation)**  
- **Feature Extraction**: Use **ORB** to extract key points.  
- **Homography Estimation**: RANSAC algorithm to align overlapping images.  
- **Blending & Stitching**: Merges images into a seamless panorama.  

---

## **3️⃣ Results & Observations**
### **Part1**  

### **Coin Detection & Segmentation Outputs:**  
- **Input Images:** Stored in `Part1/input_coins/`  
- **Edge Detection Results:** Stored in `Part1/Edges/`  
- **Contour Detection Results:** Stored in `Part1/contours/`  
- **Segmented Coins:** Stored in `Part1/segments/`  

#### **1. Preprocessing Outputs**
- **Grayscale Image:** The input image is converted to grayscale to simplify processing and reduce computational complexity. This output helps visualize intensity variations in the image.
- **Blurred Image:** A Gaussian blur is applied to smoothen the image and reduce noise. This is crucial for avoiding false edge detections.
- **Edge Detection Output:** The Canny edge detection method highlights the strong edges in the image, helping to define the boundaries of the coins.

#### **2. Contour Detection Outputs**
- **Detected Contours Image**
  - The algorithm detects coin-like contours and outlines them in **green** on the original image.
  - If a **non-circular object** is mistakenly detected, it is filtered out using contour approximation.
  - This step visually confirms which objects were recognized as coins.

#### **3. Segmentation Outputs**
- **Segmented Individual Coins**
  - Each detected coin is **isolated and saved separately** in `Part1/segments/`.
  - This helps validate if the algorithm correctly segments individual coins, even when they overlap slightly.

#### **4. Coin Counting Output**
- **Total Coins Count (Displayed in Console)**
  - The program prints the **total number of detected coins** in the console.
  - If coins are missing in the count, it indicates possible segmentation issues (e.g., overlapping coins being merged).


### **Part2** 

### **Image Stitching Output:**  
- **Input Images:** Stored in `Part2/images/`  
- **Final Panorama:** Stored as `Part2/output/stitchedOutput.png` 

#### **1. Keypoint Detection & Matching Outputs**
- **Pairwise Keypoint Matching Images (`keypoints_1_2.jpg`, `keypoints_2_3.jpg`, … )**
  - The algorithm extracts **ORB key points** from each pair of consecutive images.
  - Then to **matches key points**, RANSAC algorithm to align overlapping images.  .
  - The **good matches** are visualized with colored lines connecting similar features between two images.
  - This step helps validate whether the images have **sufficient feature overlap** for stitching.

#### **2. Stepwise Panorama Outputs**
- **Intermediate Panoramas (`panorama_1_2.jpg`, `panorama_2_3.jpg`, … )**
  - The stitching process is done **progressively**, meaning that each pair of images is merged before moving to the next.
  - If the alignment in an intermediate panorama is incorrect, it means the feature matching was inaccurate or the images did not overlap well.

#### **3. Final Stitched Panorama Output**
- **Final Panorama (`stitchedOutputProcessed.png`)**
  - After merging all images, **stitched panorama** is generated(`stitchedOutput.png`) which is further refined to get the final panaroma(`stitchedOutputProcessed.png`)
  - If an error occurs, it usually means that there wasn’t enough feature overlap between images.

---

## **4️⃣ Captured Images**  
All input images are stored in the `Part1/input_coins/` and `Part2/images/` folders for easy access.

---

## **5️⃣ Dependencies**  
The following libraries are required to run the project:  
- OpenCV  
- NumPy  
- Matplotlib  
- Scikit-image  

Install them using:  
```bash
pip install opencv-python numpy matplotlib scikit-image
```

---

## **6️⃣ Notes**  
✅ The code runs without any manual intervention.  
✅ All outputs are labeled and saved in their respective folders.  
✅ Dependencies are clearly mentioned in `requirements.txt`.  

