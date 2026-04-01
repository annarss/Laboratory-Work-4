# Laboratory Work 4 Activity 1 — Improving CNN Performance Using Regularization, Fine-Tuning, and Advanced Evaluation

# DRIVE LINK

---

# Activity 1: Evaluation Metrics + Visualization

### Classification Report
<img width="447" height="425" alt="image" src="https://github.com/user-attachments/assets/5e4aba99-6ec1-4b35-b069-99e7040175de" />


**Description:**
This report summarizes the model's accuracy through three metrics: Precision (avoiding false positives), Recall (finding all true samples), and the F1-Score (the balance of both). It highlights which specific plant species the model identifies with high confidence and where it tends to fail, such as the near-perfect scores for Anthurium compared to lower scores for more generic-looking leaves.

---

### 2. Confusion Matrix
<img width="765" height="666" alt="image" src="https://github.com/user-attachments/assets/0a598c21-29b4-44c8-821e-3a02aeb4655d" />


**Description:**
The matrix provides a visual map of the model's errors by plotting true labels against predicted labels. The bright diagonal line represents successful matches, while any values outside that line pinpoint exactly which plants are being mistaken for one another. This is crucial for identifying if two different species are visually too similar for the current CNN architecture to distinguish.

---

### 3. (ROC) Curve and Area Under the Curve (AUC) Score
<img width="712" height="605" alt="image" src="https://github.com/user-attachments/assets/7d7e4229-dd55-4a61-af4c-f18bca964a48" />


**Description:**
The ROC curve illustrates the diagnostic ability of the classifier by plotting the true positive rate against the false positive rate. The AUC (Area Under the Curve) score of 0.95 acts as a single grade for the model’s overall quality. A score this close to 1.0 indicates a highly effective model that can reliably separate different plant categories even under varying conditions.

---

### 4. Precision, Recall, F1-score per Class
<img width="1003" height="507" alt="image" src="https://github.com/user-attachments/assets/8ca645d5-a4d8-40d9-8505-f4d6a3bae226" />


**Description:**
This bar chart translates the complex numerical table of the classification report into an easy-to-read visual comparison. By looking at the height of the colored bars for each plant, you can instantly identify the "strong" classes that the model has mastered and the "weak" classes that require more data or further optimization to improve performance.

---

# Activity 2: Model Interpretability using Gradient-weighted Class Activation Mapping (Grad-CAM) - Visualizing CNN Decisions Using Grad-CAM for Explainable Image Classification


### 5. Grad-CAM Heatmap
<img width="362" height="355" alt="image" src="https://github.com/user-attachments/assets/291dd053-1849-4191-a980-688d28f065c3" />


**Description:**
The Grad-CAM Heatmap provides a visual representation of the final convolutional layer's activations, highlighting the specific "features" the model prioritized. The color intensity indicates importance, with yellow and green regions showing high-impact areas that drove the model's final classification decision for the input image.

---

### 6. Grad-CAM Overlay
<img width="337" height="357" alt="image" src="https://github.com/user-attachments/assets/a5ecd8ba-725e-4f1f-97b5-8b45d3c7f626" />


**Description:**
The Grad-CAM Overlay merges the raw heatmap with the original image of the Peace Lily to provide spatial context. This visualization confirms that the model is correctly focusing on the plant's unique botanical structures, such as the white spathe and central spadix, rather than irrelevant background elements.

---
### Grad-CAM Interpretation 

**Description:**


---

# Activity 3: Model Enhancement and Performance Optimization


### 7. Train Improved Model (17 epochs)
<img width="768" height="504" alt="image" src="https://github.com/user-attachments/assets/fe9cdb64-c6f5-42e7-9345-d830020154c5" />


**Description:**


---

### 8. Improved Classification Report
<img width="439" height="416" alt="image" src="https://github.com/user-attachments/assets/f60f97a8-ef57-437b-bca4-37186729d821" />


**Description:**


---

### 9. Improved Confusion Matrix
<img width="764" height="672" alt="image" src="https://github.com/user-attachments/assets/dea6e2da-2744-4aef-8917-6ef70f20b2ae" />


**Description:**


---

### 10. Improved (ROC) Curve and Area Under the Curve (AUC) Score
<img width="717" height="595" alt="image" src="https://github.com/user-attachments/assets/91d5469c-8a87-468a-a885-1a9fb816c1fd" />


**Description:**


---

### 11. Improved Precision, Recall, F1-score per Class
<img width="1005" height="516" alt="image" src="https://github.com/user-attachments/assets/9b4786dc-fbbe-4163-b922-f3f50e7b4145" />


**Description:**



---

### Compare Results (Before vs After)
<img width="330" height="144" alt="image" src="https://github.com/user-attachments/assets/7cb155b6-035d-4a47-a580-3c72eed62ca5" />



**Description:**


---

### 12. Visualization of Improvement
<img width="828" height="386" alt="image" src="https://github.com/user-attachments/assets/0f55ebf0-3312-4ab9-9437-9d4e8442ed67" />


**Description:**


---

## 13. GUIDE QUESTIONS
**A. Model Evaluation Analysis**
1. What were the weakest-performing classes based on the confusion matrix? Areca Palm and Philodendron Xanadu (confused with similar green foliage).
2. How did Precision, Recall, and F1-score vary across classes? Distinct plants (Boston Fern) scored high, visually similar "leafy greens" scored lower.
3. What does a low recall indicate in your model? Indicates the model is "missing" the class and mislabeling it as something else.
4. How does AUC score reflect model performance compared to accuracy? AUC shows the model's ability to distinguish classes regardless of the specific prediction threshold.

**B. Model Improvement**
5. How did data augmentation affect validation accuracy? Traded raw accuracy for "honesty," forcing the model to learn features rather than memorizing pixels.
6. Why is Batch Normalization important in CNNs? Stabilized training, allowing for faster convergence and smoother gradient flow.
7. What role did Dropout play in improving your model? Prevented overfitting by forcing the network to learn redundant, robust features.
8. How did Early Stopping prevent overfitting? Terminated training at Epoch 17 to prevent the model from learning "noise" in the data.
 
**C. Performance Comparison**
9. What improvements were observed after modifying the model? Enhanced generalization; the model handles variety (rotations/zooms) much better.
10. Which enhancement contributed the most to performance improvement? Why? Data Augmentation, as it shifted the model from rote memorization to actual recognition.
11. Did the gap between training and validation accuracy decrease? Explain. Yes, the gap narrowed. Val Acc is greater than Train Acc proves the model is generalized.

**D. Explainability (Grad-CAM Integration)**
12. How did Grad-CAM help in understanding model predictions? Confirmed the model "looks" at botanical features (flowers/leaves) rather than the background.
13. Did the improved model focus on more relevant regions? Provide evidence. Heatmaps were concentrated on unique identifiers like the Peace Lily's spathe.
14. Why is explainability important in real-world AI applications? Critical for trust, ensures the AI makes decisions based on relevant data, not coincidental patterns.

---

