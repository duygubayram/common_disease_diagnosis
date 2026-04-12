# common_disease_diagnosis

This is a project I chose for its challenging aspect. It contains a kaggle dataset of common diseases with common symptoms (eg. allergy, fever), the data is synthetic with 30 disease classes and 28 unique symptoms. The symptom overlap and number of classes make this task challenging for an AI model to learn.

The data analysis notebook is uploaded. The training notebooks will be uploaded soon when documentation is complete and the code is clean.

As a summary, so far I have tried:
1. Straightforward fine-tuning: Disease with all symptoms listed.
2. Fine-tuning with symptom pairs (cough-sneezing more likely to be allergy than fever-sneezing)
3. Fine-tuning with class weights (more common symptoms - less weight)
4. Grouping diseases and symptoms to reduce grain
5. Fine-tuning with age and gender information added to the symptoms list

All tried on a BERT model fine-tuned on the medical domain. I have tested some hyperparameters, but the models seem to collapse at even 50 epochs. 

I have additionally implemented the Random Forest approach as I believe the lack of pattern in this synthetic data (eg. gender and age serve no differentiating factor) proposes a challenge for LMs to learn to differentiate between different classes. As expected, this is the only model that has not collapsed, although the F1 score is still low.

Others who have tried also stayed around 4%, my grouping approach increased F1 to 11% although this is artificial because of the collapsed classes. Best performance is from Random Forest at 16%.
