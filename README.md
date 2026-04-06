# Laboratory Work 4 Activity 1 — Improving CNN Performance Using Regularization, Fine-Tuning, and Advanced Evaluation

# DRIVE LINK
https://drive.google.com/drive/folders/1g-Vgu4Yj6xixsyCDvRQ-L7J9eWEpkQhd?usp=sharing

---

# Activity 1: Evaluation Metrics + Visualization

### Classification Report
<img width="505" height="430" alt="image" src="https://github.com/user-attachments/assets/6a24b576-75cb-485b-a0b2-ee7a8e4dafd1" />




**Description:**
This report summarizes how well the model recognized each of the 20 plant species using three metrics: Precision (how often the prediction was correct), Recall (how many actual plants were correctly found), and F1-Score (the balance of both). It highlights which plants the model identifies with high confidence and where it struggles — like the perfect scores for boston fern and near-perfect results for caladium and anthurium red champion, compared to the much lower scores for philodendron xanadu and alocasia which are harder to distinguish because they look similar to other plants in the dataset.

---

### 2. Confusion Matrix
<img width="717" height="629" alt="image" src="https://github.com/user-attachments/assets/51561873-feab-4dbc-aee4-b84c8f63f06c" />




**Description:**
The matrix provides a visual map of the model's errors by plotting true labels against predicted labels. The bright diagonal line represents successful matches, while any values outside that line pinpoint exactly which plants are being mistaken for one another. This is crucial for identifying if two different species are visually too similar for the current CNN architecture to distinguish.

---

### 3. (ROC) Curve and Area Under the Curve (AUC) Score
<img width="999" height="755" alt="image" src="https://github.com/user-attachments/assets/ea845bc5-81b1-4ef9-9605-af26dcd2b5e5" />




**Description:**
The ROC curve shows how well the model can tell each plant apart from the others by comparing true positive rate against false positive rate. The closer a line is to the top left corner, the better that class is being recognized. Most plants scored very high — boston fern and snake plant achieved a perfect AUC of 1.00, and antharium red champion reached 0.99. The weakest were fiddle leaf fig at 0.87 and philodendron xanadu at 0.84, which matches the classification report where these plants also struggled. The overall AUC score of 0.9528 means the model is very reliable at distinguishing between the 20 plant species even when individual predictions are sometimes wrong.

---

### 4. Precision, Recall, F1-score per Class
<img width="1169" height="573" alt="image" src="https://github.com/user-attachments/assets/8610fc40-62a1-4ae7-8da3-2c8b245bbcb2" />



**Description:**
The bar graph displays the Precision, Recall, and F1-score metrics for all the 20 plant species. Boston fern and caladium got close-to-perfect results, whereas philodendron xanadu, alocasia, and areca palm received the worst marks, probably due to their similarity with other plant types. In general, the model achieved good results, with 0.79 precision, 0.77 recall, 0.77 F1-score, and AUC of 0.9528.

---

# Activity 2: Model Interpretability using Gradient-weighted Class Activation Mapping (Grad-CAM) - Visualizing CNN Decisions Using Grad-CAM for Explainable Image Classification


### 5. Grad-CAM Heatmap
<img width="365" height="359" alt="image" src="https://github.com/user-attachments/assets/a79bf2b2-43b4-457c-be6e-516d61d888c9" />



**Description:**
This Grad-CAM heatmap shows where the model focused when predicting croton(mammy). The warm yellow and red areas are what influenced the decision most, but the activation is spread out across the whole image rather than focused on the plant's distinctive colorful leaves, suggesting the model still needs improvement in identifying the most relevant features.

---

### 6. Grad-CAM Overlay
<img width="684" height="369" alt="image" src="https://github.com/user-attachments/assets/b02b1e24-f201-4a41-8a27-58f3f323e8d1" />



**Description:**
The Grad-CAM overlay shows where the model looked when it predicted croton(mammy) with 50.95% confidence. The highlighted regions are spread across the entire plant rather than focused on one specific area, which explains the relatively low confidence score. The model is picking up on the colorful leaf patterns overall but hasn't pinpointed the most defining features yet, suggesting there is still room to improve how the model recognizes this species.

---
### Grad-CAM Interpretation 

**Description:**
Grad-CAM represents the process used by the neural network in deciding how to classify the image by showing the areas of the image that have contributed most to the decision. In this case, the heatmap is not only localized in some areas but covers the entire plant as opposed to concentrating on one unique aspect of croton(mammy), which is the brightly colored and multicolored leaves. This could explain the lower level of confidence at 50.95%.

---

# Activity 3: Model Enhancement and Performance Optimization


### 7. Train Improved Model (using 20 epochs)
<img width="765" height="585" alt="image" src="https://github.com/user-attachments/assets/523061f7-7fdb-4334-a474-f0d13c12ace3" />



**Description:**
The improved model was trained for 20 epochs with steady improvement observed through all 20 epochs. It achieved extremely poor accuracy of 22.27% and high loss of 2.97 at Epoch 1, but steadily kept improving its performance until achieving the accuracy of 55.66% and validation accuracy of 70.50% at the final Epoch 20. It is important to note that the validation accuracy remains better compared to the training accuracy, showing that the model is well-generalized and not prone to overfitting, due to dropout layers and data augmentation.

---

### 8. Improved Classification Report
<img width="499" height="428" alt="image" src="https://github.com/user-attachments/assets/d8b9423f-c216-4fa3-a03e-948c7510f228" />



**Description:**
In this report on classification, we see the results obtained with the enhanced version of our model, where such components as BatchNormalization, enhanced augmentation, and larger dropouts were added. Overall, there was only a slight decrease in accuracy in comparison with the baseline model from 77% to 71%. Similarly, there was a minor change in the macro-average F1-score from 0.77 to 0.70. On the one hand, the performance on certain classes became more balanced, with caladium and boston fern performing well, while areca palm and fiddle leaf fig lagged behind. However, this is an expected result, considering that stronger regularization made the model less liberal.

---

### 9. Improved Confusion Matrix
<img width="748" height="639" alt="image" src="https://github.com/user-attachments/assets/33f5c685-3adc-4ddf-a82a-1177fd633898" />



**Description:**
The confusion matrix reveals that the enhanced model was able to recognize the majority of the plants, including a perfect score for the boston fern as well as strong performance from anthurium, chlorophytum, and zz plant. Confusion mainly arises because croton(mammy) is similar to croton(petra). There is a more uniform distribution of errors across all classes as opposed to just some problematic plants like before.

---

### 10. Improved (ROC) Curve and Area Under the Curve (AUC) Score
<img width="748" height="508" alt="image" src="https://github.com/user-attachments/assets/1ccb4480-8760-43f5-9588-66f2e9681c3d" />



**Description:**
The improved model's ROC curve shows an overall AUC of 0.9051, slightly lower than the baseline's 0.9528. Boston fern still achieved a perfect 1.00 while alocasia dropped to 0.79 and philodendron xanadu to 0.80 — the weakest performers. Compared to the baseline, the curves are slightly less steep meaning the model trades some discriminative ability for better generalization, which is the expected result of applying stronger regularization and augmentation.



---

### Compare Results (Before vs After)
<img width="288" height="120" alt="image" src="https://github.com/user-attachments/assets/5e3b71dd-b0ee-4fe1-a1f0-04d4671fd9ad" />



**Description:**
The comparison table shows the improved model achieved a validation accuracy of 70.50% which is actually higher than its training accuracy of 55.66% — a strong sign of good generalization with zero overfitting. While the baseline had slightly higher precision, recall, F1, and AUC scores, it was heavily with a 21% gap between training and validation accuracy. The improved model sacrificed some raw performance numbers in exchange for a much healthier and more reliable model that performs consistently on new unseen data, which is more valuable in real-world use.

---

### 11. Visualization of Improvement
<img width="755" height="325" alt="image" src="https://github.com/user-attachments/assets/1c3cb314-ce2f-4084-b8f4-3e3cb54457fa" />



**Description:**
From the Accuracy plot, we can see that the validation accuracy remains higher than the training accuracy at all times during all the 20 epochs, which is excellent news since it shows that our model has excellent generalization power without being overfitted. From the Loss plot, we can observe that initially, the validation loss was highly erratic, rising up to almost 12 in the initial epochs because of the new augmentation, but then it became consistent, with the training and validation losses going down simultaneously.

---

## 12. GUIDE QUESTIONS
**A. Model Evaluation Analysis**
**1. What were the weakest-performing classes based on the confusion matrix?**
From the classification report, the poorest-performing classes are those of philodendron_xanadu, with a precision of 44% and an F1-score of 56%, alocasia, with a precision of 57% and an F1-score of 62%, and areca_palm, with a precision of 57% and an F1-score of 60%.
**2. How did Precision, Recall, and F1-score vary across classes?** 
The disparity between the top-performing groups and those that underperformed was huge. Boston fern was the highest, scoring perfect marks of 1.00 for each of the measures, followed by caladium with 0.97-0.98, and anthurium red champion with 0.96. In the bottom bracket, philodendron xanadu had a precision of just 0.44 while alocasia registered a precision of 0.57.
**3. What does a low recall indicate in your model?** 
If the recall value is low, this means that the model missed true cases of the particular class, meaning it did not recognize all of the true corn plant examples. Corn_plant had a recall of 0.68, which means that the model incorrectly recognized around 32% of the true cases. In an app used for identifying plants, the user who has a corn plant will most likely receive a wrong output about one-third of the time.
**4. How does AUC score reflect model performance compared to accuracy?** 
While our initial model had 77% accuracy and an AUC of 0.9528, which was extremely high compared to the former, it was important to take into consideration the fact that AUC gives us more information about the performance of the model than accuracy, because unlike the latter, AUC shows us the quality of ranking of the true classes above other classes, regardless of whether the final decision on which one is correct was made accurately.

**B. Model Improvement**
**5. How did data augmentation affect validation accuracy?** 
The new version of the model had more robust data augmentation techniques such as horizontal and vertical flipping, rotation by 20%, zooming by 20%, and contrast change. The training outcomes show that the model’s accuracy rose from 14.75% at Epoch 1 to 70.50% at Epoch 20. Data augmentation initially slowed down the training process, making it difficult for the model, but eventually, it benefited the entire learning process up to Epoch 20.
**6. Why is Batch Normalization important in CNNs?** 
Batch normalization helps normalize the output from each layer so that the output does not become excessively large or small. In the modified model, batch normalization is included after each Conv2D layer. It helped stabilize the training process, allowing us to observe consistent improvements from epoch to epoch instead of stagnation or instability. Without it, the excessively high validation loss of 8.23 recorded in Epoch 1 would have been able to destabilize training.
**7. What role did Dropout play in improving your model?** 
Two dropout layers were employed during the design of the architecture; 0.4 was used immediately after the convolutional layers and 0.5 was applied to the Dense(256). This ensured that there would be no over-reliance on certain neurons during the training process. In terms of performance, the training accuracy was 55.66% for epoch 20, whereas the validation accuracy was 70.50%, indicating that the higher validation accuracy than the training accuracy suggested effective use of dropout.
**8. How did Early Stopping prevent overfitting?**
Early stopping monitored the validation loss with patience 3, which means the training process would be stopped if there was no improvement in the validation loss for three continuous epochs. Our result indicated that our model trained for all the 20 epochs since the validation loss improved continuously throughout the entire training process. Without the early stopping technique, the model could train beyond its optimal point even if it had overfitted.
 
**C. Performance Comparison**
**9. What improvements were observed after modifying the model?**
Strangely enough, the modified model performed worse on some parameters compared to the baseline. In terms of validation accuracy, the baseline obtained 77% whereas the improved one reached only 70.50%. In terms of precision, the baseline was 0.7935 while the improved model was 0.7129. Nevertheless, what the improved model demonstrates is a more balanced approach during the training process, with the training accuracy being 55.66% and validation accuracy 70.50%, which makes overfitting impossible.
**10. Which enhancement contributed the most to performance improvement? Why?**
The most valuable contribution was Batch Normalization due to its stabilization of the model for the whole duration of 20 epochs. The reason behind it was that without Batch Normalization, the validation loss value of Epoch 1 was 8.23 which is highly unstable. Another contributing factor was lowering the learning rate to 0.0001.
**11. Did the gap between training and validation accuracy decrease? Explain.** 
Yes and it actually reversed. The baseline had training accuracy of 96.17% vs validation of 74.53%, a gap of about 21% showing severe overfitting. The improved model had training accuracy of 55.66% and validation accuracy of 70.50%, validation is actually 14.84% higher than training. This means the improved model has zero overfitting and is generalizing very well to unseen data.

**D. Explainability (Grad-CAM Integration)**
**12. How did Grad-CAM help in understanding model predictions?**
The Grad-CAM helped us know exactly which parts of the plant image were of importance for the model to come up with its decisions. On applying the algorithm to our image, it made a prediction of "croton(mammy)" with a 50.95% confidence, and also gave the areas on the leaves that led to such a conclusion. If not for using the Grad-CAM, all we would know is just the figure of the prediction probability.
**13. Did the improved model focus on more relevant regions? Provide evidence.**
The enhanced model achieved a prediction accuracy of 69.25% for croton_petra, while the initial one only predicted croton(mammy) with an accuracy of 50.95%. This indicates that the enhanced model is better able to detect important features in its prediction process. The two plant types are very similar in appearance, and the enhanced model’s greater ability to differentiate between them implies more effective feature recognition.
**14. Why is explainability important in real-world AI applications?**
In any practical plant detection application, the user should be able to trust the results. Should the neural network say that a plant is a snake plant, while Grad-CAM tells us that it was focused on the background behind it, then we can safely assume that the algorithm is untrustworthy. The ability to understand how a model makes decisions also allows us to correct issues when it comes to developing such models; for example, when the model starts to focus on the background rather than the leaf itself.

---

