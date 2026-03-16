
# ☀️ Solar Panel Defect Classifier

An end-to-end deep learning project that automatically classifies the condition of solar panels from images. This tool helps identify maintenance needs such as physical damage, electrical damage, or environmental obstructions like snow and dust, ultimately assisting in maintaining optimal energy output.

## 📊 Dataset & Classes
The model was trained on a dataset of **885 images** (708 training, 177 validation) categorized into **6 distinct classes**:
* `Bird-drop`
* `Clean`
* `Dusty`
* `Electrical-damage`
* `Physical-damage`
* `Snow-Covered`

## 🧠 Modeling Approach & Performance
Multiple architectures were evaluated to find the optimal balance between training accuracy and generalization (validation accuracy):

1.  **Baseline Custom CNN2D:** * Parameters: ~11.1M
    * Result: Suffered from severe overfitting (Training Accuracy: 99.80%, Validation Accuracy: 61.02%).
2.  **Transfer Learning (MobileNetV2):**
    * Parameters: ~2.4M
    * Result: Reduced overfitting but underperformed on feature extraction (Validation Accuracy: 65.54%).
3.  **Transfer Learning (EfficientNet):** * Parameters: ~4.2M
    * Result: Superior feature extraction and balance (Validation Accuracy: 79.66%).
4.  **Final Model (Fine-tuned EfficientNet + Hyperparameter Optimization):**
    * **Result: Achieved the best validation accuracy of 83.05%.**

## 🚀 Deployment
The model is served via an interactive web application built with **Streamlit**. Users can upload images (JPG/PNG) and receive instant predictions, confidence scores, and a breakdown of the top 3 most likely conditions.

### Installation & Local Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/captainKLSH/Solar-Panel-Defect-CNN-Classifier-2023
   cd Solar-Panel-Defect-CNN-Classifier-2023
   ```

2. Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```
3. Install the required dependencies:

```bash
pip install -r requirements.txt
```
3. Run the application:

```bash
python3 -m streamlit run app.py
```
4. Server Deployment (Linux)
To run the app continuously in the background on a Linux server:
```bash
#Permanent running
nohup python3 -m streamlit run app.py
```
