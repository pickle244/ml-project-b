# ml-project-b

Authors: Jeffrey Li and Peter Llamas

Purpose: A classifier to identify whether a patient with skin lesions should
receive medical treatment.

Dataset: https://pmc.ncbi.nlm.nih.gov/articles/PMC7479321/
An 80/20 split was used to separate training and testing data. There is no
overlap in patients across the two splits.

Design: We adapted efficientnet_b0, a pretrained Pytorch Convolutional Neural
Network, to generate image embeddings from the lesion images and then trained a
Random Forest Classifier to make predictions. Next, we split the tabular patient
data by ages <60 and 60+ and trained a separate RFC for both age groups. The
final prediction was an average of the two RFCs. Overall, the prediction was an
average of the embedding predictions and feature predictions.

Performance: The model was evaluated on AUCROC, and we achieved a score of
0.91623. We also evaluated AUCROC on three age groups: <30, 30-60, and 60+. Our
worst-performing age group was 60+, with a score of 0.86861.