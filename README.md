# CBCIC2020

This repository was created to present our results for the CBCIC2020 competition.

https://sites.google.com/view/bci-comp-wcci/

https://github.com/5anirban9/Clinical-Brain-Computer-Interfaces-Challenge-WCCI-2020-Glasgow

The results were obtained using the developed software, which at present cannot be published in the public domain.


Classification methodology

All work was done using python 3.6.

(A)  within subject classification (P01 - P08) 

1. Each 8-second trial was filtered at 4-38 Hz (filtfilt, butter IIR 4 order).
2. Each 8-second trial was baselined (baseline 0-4 sec).
3. The first 3 seconds were cut off from each trial (8-sec -> 5 sec).

4. The 80 original training trials were divided into training and test sets (40/40).

5. The FBCSP-SVM classifier was trained on a training set and validated on a test set (using Cohen's kappa as a metric).

6. Step (5) was repeated several times using the custom algorithm for fine-tuning the parameters of the FBCSP-SVM classifier.

7. The parameters of the classifier that showed the highest kappa in step (6) were used to tune the final FBCSP-SVM classifier set up.

8. The classifier set up made in step (7) was trained on a randomly selected 50% of the 80 original training trials, and run to predict on the evaluating data (40 unlabeled trials).

9. Step (8) was repeated 100 times and the predicted labels were added to the results table.

10. The results of step (9) were averaged: if the average value are <= 1.5 the label class=1 is set, if the average value are > 1.5  the label class=2 is set.

(B) cross subject classification (P09, P10) There was used the same pipeline as in (A), but for training/validation of FBCSP-SVM classifier, we used the all labeled data of patients P01-P08, (80 trials * 8 subjects) = 640 trials.
