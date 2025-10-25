# AI-Powered-Enhanced-EHR-Imaging-Documentation-System

### 📘 Module 1 – Data Collection & Preprocessing  

---

## 🔍 Overview
This module focuses on the **collection, cleaning, encoding, and preparation** of both structured and unstructured healthcare data.  
It forms the foundation for subsequent modules like **Medical Image Enhancement (Module 2)** and **AI-based Disease Prediction (Module 3)**.

The main goal is to build a clean, consistent, and machine-readable dataset that integrates various healthcare sources such as:
- Patient medical records  
- ICD-10 diagnostic codes  
- Doctor’s handwritten prescriptions (image data)  
- Chest X-ray images  

---

## 🎯 Objectives
- Collect and preprocess structured (CSV) and unstructured (image/text) data  
- Handle missing values, duplicates, and inconsistent data formats  
- Encode categorical columns for machine learning compatibility  
- Scale numerical features for model stability  
- Generate synthetic links between patient records, prescriptions, and X-ray data  
- Save all cleaned datasets for use in later modules  

---

## 🧩 Datasets Used
| Dataset Name | Type | Description |
|---------------|------|-------------|
| **Healthcare Dataset** | Structured | Contains patient details like age, gender, condition, admission details, and test results |
| **ICDCodeSet.csv** | Structured | Contains ICD-10 medical codes and disease descriptions |
| **Doctor’s Handwritten Prescription BD Dataset** | Unstructured (Images) | Handwritten prescription images used for OCR and text recognition |
| **X-ray Dataset** | Unstructured (Images) | Chest X-ray images for later enhancement and diagnosis |

---

## ⚙️ Data Preprocessing Steps

### 1️⃣ Environment Setup  
Imported necessary libraries including `pandas`, `numpy`, `matplotlib`, `seaborn`, and scikit-learn preprocessing modules.

### 2️⃣ Data Loading  
Loaded all structured and unstructured datasets from `/content/` or Google Drive and inspected their structure.

### 3️⃣ Data Cleaning  
- Checked for missing values  
- Filled missing numeric values with median/mode  
- Converted date columns into `Stay_Duration` (Discharge − Admission)  
- Dropped irrelevant columns such as Name, Doctor, Hospital, etc.

### 4️⃣ Data Encoding & Scaling  
- Encoded categorical variables (Gender, Blood Type, Admission Type, etc.) using `LabelEncoder`  
- Scaled numerical values using `StandardScaler`  

### 5️⃣ ICD Dataset Preparation  
- Removed duplicates  
- Cleaned column names  
- Created a mapping dictionary for ICD codes  

### 6️⃣ Prescription Dataset Processing  
- Created dataframes for `train`, `test`, and `validation` splits  
- Generated image paths and unique prescription IDs  

### 7️⃣ X-ray Dataset Processing  
- Indexed image paths for X-ray splits (train/test/val)  
- Stored class labels and IDs  

### 8️⃣ Synthetic Linking  
- Randomly associated each patient record with `prescription_id` and `xray_id`  
- Ensured consistent linkage for later modules  

### 9️⃣ Saving Cleaned Data  
Exported the following cleaned CSV files:
- `cleaned_healthcare_dataset.csv`  
- `cleaned_icdcodeset.csv`  
- `cleaned_prescription_dataset.csv`  
- `cleaned_xray_index.csv`

---

## 📊 Exploratory Data Analysis (EDA)
Performed post-cleaning validation to ensure:
- No missing or duplicate values remain  
- Encoded data distributions are balanced  
- Numerical features are properly scaled  
- Correlations between attributes are visualized through heatmaps

---

## 📁 Output Directory Structure

<img width="453" height="423" alt="Screenshot 2025-10-21 150800" src="https://github.com/user-attachments/assets/998bcb5a-36e7-47ba-825f-f6ef0e61b6e1" />



---

## ✅ Module-1 Results Summary
- Structured and unstructured datasets successfully preprocessed  
- Patient records are standardized and machine-readable  
- Clean datasets saved for Module 2 (Medical Image Enhancement)  
- Dataset linkage between EHR, prescriptions, and X-rays established  

---

# 🩻 Module 2: Medical Imaging Enhancement

## 🎯 Objective
Enhance the quality of medical images — **X-rays** and **handwritten prescriptions** — using traditional image processing techniques to improve visibility, contrast, and diagnostic usability before AI model training.

---

## ⚙️ Methods Used

This module applies multiple enhancement and preprocessing techniques to the images to ensure uniformity and high diagnostic quality.

| Technique | Description |
|------------|--------------|
| **CLAHE (Contrast Limited Adaptive Histogram Equalization)** | Enhances local contrast and brightness. |
| **Gaussian & Bilateral Filtering** | Reduces image noise while preserving edges. |
| **Unsharp Masking** | Improves fine structural and text details. |
| **Normalization** | Maintains consistent intensity across all datasets. |

---

## 🧪 Evaluation Metrics

To validate the quality of the enhanced images, the following quantitative metrics were computed:

| Metric | Description | Ideal Range |
|---------|--------------|--------------|
| **PSNR (Peak Signal-to-Noise Ratio)** | Measures how much noise was removed — higher is better. | > 20 dB |
| **SSIM (Structural Similarity Index)** | Evaluates visual similarity and structural fidelity — closer to 1 is better. | > 0.70 for X-rays, > 0.85 for Prescriptions |

---

## 📈 Results Summary

| Dataset | PSNR (avg) | SSIM (avg) | Remarks |
|----------|-------------|-------------|----------|
| **X-ray Images** | 20.94 | 0.685 | Good quality; slightly improvable with mild sharpening. |
| **Prescription Images** | 21.266 | 0.891 | Excellent enhancement and readability. |

---

## 📁 Output Files

| File/Folder | Description |
|--------------|--------------|
| `/content/enhanced_images/` | Folder containing all enhanced X-ray and prescription images. |
| `/content/cleaned_data/enhanced_image_index.csv` | CSV containing image paths with PSNR and SSIM scores. |
| `/content/cleaned_data/module2_summary.txt` | Text summary of all enhancement metrics. |

---

## 🧩 Integration Notes
- These enhanced images will be **used as input for Module 3**, where AI models will be trained for disease prediction and diagnostic support.
- The improvement in contrast and clarity ensures that **ML and CNN-based models** can extract better features from images.
- The enhanced datasets maintain compatibility with the cleaned structured data generated in **Module 1**.

---

## 📊 Visual Comparison
Below is a sample before-and-after visualization generated during the enhancement process:

## 🩻 X-ray Images: Before vs After Enhancement

| Original Image | Enhanced Image |
|----------------|----------------|
| <img src=<img width="358" height="259" alt="Screenshot 2025-10-25 121559" src="https://github.com/user-attachments/assets/08e13357-5993-4a7c-b77f-a90b7b47a79c" />
> | <img src=<img width="360" height="256" alt="Screenshot 2025-10-25 121628" src="https://github.com/user-attachments/assets/47701af7-766f-4305-a76e-bc627069efef" />
> |


## 📝 Prescription Images: Before vs After Enhancement

| Original Image | Enhanced Image |
|----------------|----------------|
| <img src=<img width="346" height="197" alt="Screenshot 2025-10-25 121646" src="https://github.com/user-attachments/assets/344fb232-2c0c-4734-ab0d-dfc1ae75f3b9" />
> | <img src=<img width="334" height="180" alt="Screenshot 2025-10-25 121659" src="https://github.com/user-attachments/assets/f4865b64-23b6-4a7d-bc83-dbd82b4c93db" />
> |


---

## 🧠 Key Learnings
- Image enhancement improves **diagnostic interpretability** before AI model training.
- PSNR and SSIM are effective metrics to evaluate **image restoration and denoising quality**.
- Proper preprocessing significantly influences **AI model accuracy** in later stages.

---

## ✅ Module-2 Results Summary

- X-ray and Prescription image datasets successfully enhanced and denoised  
- Applied CLAHE, Bilateral Filtering, Gaussian Smoothing, and Unsharp Masking for visual clarity  
- Achieved strong quality metrics for medical image usability  
- Average X-ray quality → PSNR: **20.94**, SSIM: **0.685**  
- Average Prescription quality → PSNR: **21.266**, SSIM: **0.891**  
- Enhanced images saved to `/content/enhanced_images/`  
- Quality metrics and summary stored in `/content/cleaned_data/`  
- Outputs ready for Module 3: **AI-based Medical Image Analysis and Prediction**


---


