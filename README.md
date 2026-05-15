# RAYON_Laboratory_Work5_Activity-Comparative-Analysis-of-Pre-trained-CNN-Models-
## Submitted By:
Candy Apple Clair L. Rayon
## Collab Link
[Click here to view the collab]
([https://drive.google.com/file/d/1rnZIRPWHnqRvWl19_oFTxCvNZY59gD2b/view?usp=drive_link](https://colab.research.google.com/drive/1MFVSgeH1Kmqp18Z7czYJclw9BtZCFzvJ?usp=sharing))


**PART 12: Performance Comparison Table**


-------------------------------------------------**GUIDE QUESTIONS (FINAL REFLECTION)**------------------------------------------------------------

PART 12: Performance Comparison Table

<img width="1300" height="422" alt="Screenshot 2026-05-15 233600" src="https://github.com/user-attachments/assets/18861d6d-2b07-46dd-8ed9-fb05513f2951" />


**A. Model Performance**

**1. Which pre-trained model achieved the highest accuracy? Why?**
  
  -  MobileNetV2 got the highest score — 83.60% validation accuracy. It did so well because it was built to be both fast and smart. It uses a special design that lets it pick up important details        from images without needing a lot of computing power. Even when we froze most of its layers (transfer learning), it still learned our custom dataset better than the others.

**2. Which model had the lowest performance? What could be the reason?**

  - EfficientNetB0 and EfficientNetB3 were the worst both stayed near random guessing the whole time (around 3–4% accuracy). ResNet50 also performed poorly at only 11%. The most likely reason is        that these models expect images to be prepared in a specific way before being fed to them, but our notebook applied a generic rescaling step that conflicted with that expectation. Because of        this mismatch, the models could never properly "see" the images the way they were designed to.

**3. How did loss values compare across models?**

  - Models that actually learned showed their loss numbers going down steadily over 10 epochs. MobileNetV2 dropped from about 2.84 all the way down to 0.76. DenseNet121 and Xception also dropped        significantly. But the models that failed like EfficientNetB0 and ResNet50 barely moved at all, staying stuck near 3.0 the whole time. A stuck loss means the model learned nothing. VGG16            was in the middle it improved slowly but never got close to the top performers.


**B. Evaluation Metrics**

**4. Why is accuracy not enough to evaluate a model?**

  - Accuracy just tells you how many answers were correct overall. But it can be misleading. For example, if one class is much easier to recognize, the model might just keep guessing that class and     still look like it's doing well. Metrics like Precision, Recall, and F1-score show how well the model does on each class individually, which gives a much more honest picture of its true             performance.

**5. Which model had the best F1-score? What does it indicate?**

  - MobileNetV2 would have the best F1-score, matching its top accuracy of 83.60%. A good F1-score means the model is both good at avoiding wrong guesses (precision) and good at not missing correct     ones (recall). In short, it means the model is consistently reliable across all 20 classes not just lucky on easy ones.

**6. How did Precision and Recall differ across models?**

  - The top models (MobileNetV2, DenseNet121, Xception) would show solid precision and recall across most classes. The failing models like EfficientNetB0 would show near-zero recall for almost          every class — meaning they basically never correctly identified anything. They may have just predicted the same class over and over. VGG16 showed some improvement but still missed many correct      predictions, so its recall would be lower than its precision.


**C. Confusion Matrix Analysis**

**7. Which classes were frequently misclassified?**

  - Without the full report, we can infer that visual similarity is the main cause of errors. For a weaker model like ResNet50, misclassifications occur across almost all categories. In contrast, a     stronger model like MobileNetV2 only makes errors on the most similar and challenging classes.

**8. What patterns did you observe in the confusion matrix?**

  - For the good models, most of the numbers line up along the diagonal which means the model got most predictions right. Errors appear off to the sides, between similar-looking classes. For the        bad models like EfficientNetB0, most of the numbers pile up in one or two columns, which means the model kept predicting the same class no matter what image was shown a clear sign something         went wrong.


**D. ROC and AUC**

**9. Which model had the highest AUC score?**

  - MobileNetV2 would have the highest AUC score, since it also had the best accuracy and loss. DenseNet121 and Xception would be close behind. The failing models (EfficientNetB0, EfficientNetB3,       ResNet50) would have AUC scores near 0.5, which means they're no better than a coin flip.

**10. What does AUC tell us about model performance?**

  - AUC tells us how well a model can tell one class apart from another. A score of 1.0 is perfect the model always knows the right answer. A score of 0.5 means it's just guessing randomly. The         higher the AUC, the more confident and correct the model is when choosing between classes. It's useful because it works well even when some classes have more images than others.


**E. Explainability (Grad-CAM)**

**11. What did Grad-CAM reveal about model decision-making?**

  - Grad-CAM creates a heat map on top of the image that shows where the model was "looking" when it made its prediction. It showed which parts of the image had the most influence on the model's        decision like if it was focusing on the main object in the photo or getting distracted by the background.

**12. Did the model focus on relevant image regions?**

  - If the heat map highlighted the main subject of the image (the actual object being classified), then yes — the model was paying attention to the right thing. If the heat map was spread all over     random areas, it means the model was relying on irrelevant parts of the image, like background textures or colors, which would hurt its real-world usefulness.

**13. Which model produced the most meaningful heatmaps?**

  -  Grad-CAM was applied to the custom CNN. Among the pretrained models, MobileNetV2 being the best performer would produce the clearest and most focused heatmaps, since it learned the most useful      features. The models that barely trained (like EfficientNetB0) would produce blurry, meaningless heatmaps because their features never really adapted to the custom dataset.

**F. Model Comparison & Improvement**

**14. Which model would you recommend for deployment? Why?**

  - MobileNetV2 is the best choice. It had the highest accuracy (83.60%), the lowest loss, and it's also lightweight and fast meaning it won't need a powerful computer to run. It's designed to        work well even on phones or small devices. It also kept improving throughout all 10 training epochs, which means it still has room to get even better

**15. How can you further improve your best-performing model?**

  - **Unfreeze some layers** — let more of the model learn from your specific dataset instead of keeping it frozen.
    **Add image augmentation** — randomly flip, rotate, or brighten training images so the model sees more variety and doesn't just memorize.
    **Train longer** — the model was still improving at epoch 10, so training for 20–30 epochs would likely push accuracy higher.
    R**educe the learning rate over time** — this helps the model fine-tune itself more carefully as it gets better.
    **Make sure classes are balanced** — having roughly the same number of images per class helps the model treat all classes fairly.


**G. Real-World Application**

**16. How can your model be applied in real-world scenarios?**

  - **Smart Herbal Assistants**: Powering mobile apps that help users identify medicinal plants in their own gardens or in the wild, providing immediate information on their traditional uses and        benefits.

    **Quality Control in Herbal Medicine**: Assisting pharmacists or herbalists in verifying raw plant materials to ensure that the correct species is being used for supplements or traditional          remedies, reducing the risk of using "look-alike" toxic plants.
    
   ** Agricultural Monitoring**: Helping farmers or botanists automate the sorting and cataloging of harvested medicinal crops in large-scale production facilities.
    
   **Educational Tools for Conservation**: Supporting students and researchers in the field by providing a quick way to document and classify rare or endangered medicinal species for biodiversity      databases.
      
   **Inventory Management for Natural Pharmacies**: Streamlining the organization and tracking of various dried or fresh plant stocks in stores that specialize in natural medicine.

**17. What are the risks of deploying an inaccurate model?**

  - **Wrong results** — the model gives incorrect predictions, which can cause real problems depending on what it's used for.
    **Loss of trust** — users stop relying on the app if it keeps getting things wrong.
    **Unfair outcomes** — if the model was trained on limited data, it might consistently fail on certain groups or categories.
   ** Wasted money or resources** — in business or industrial settings, wrong classifications lead to costly mistakes.
   ** Danger in critical uses** — if used in healthcare or safety systems, a wrong prediction could seriously harm someone.

**18. How can this system be integrated into a mobile/web app?**

  - Web app: Save the model, build a simple website using Flask or FastAPI where users upload a photo, and the model tells them what it sees.
    Mobile app: Convert the model to a smaller format (TensorFlow Lite) that can run directly on a phone no internet needed.






    


