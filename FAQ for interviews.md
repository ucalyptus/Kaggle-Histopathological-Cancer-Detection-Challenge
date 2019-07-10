## Why I used AUC-ROC instead of Accuracy?
AUC stands for Area Under the Curve, which curve you ask? Well, that would be the ROC curve.
ROC stands for Receiver Operating Characteristic, which is actually slightly non-intuitive.
The implicit goal of AUC is to deal with situations where you have a very skewed sample distribution,
and don't want to overfit to a single class.
A great example is in spam detection. 
Generally, spam datasets are STRONGLY biased towards ham, or not-spam. 
If your data set is 90% ham, you can get a pretty damn good accuracy by just saying that every single email is ham,
which is obviously something that indicates a non-ideal classifier. 

## Differentiate AUC ROC with F1-Score?
The biggest difference is that you don't have to set a decision threshold with AUC
(it's essentially measuring the probability spam is ranked above non-spam).
F1-score requires a decision threshold.Of course, you could always set the decision threshold as an operating parameter and plot F1-scores.

## What is Softmax and how is it different from Sigmoid?

In general, when you have a problem where the sample can only belong to one class among a set of classes, you set the last layer to be a soft-max layer. It allows you to interpret the outputs as probabilities. When using a soft-max layer, 
cross entropy generally works very well, because the logarithmic term in the cross-entropy cancels out the plateau that is 
present in the soft-max function, therefore speeding up the learning process (think of points far away from 0 in the sigmoid function).

In your case you have a binary classification task, therefore your output layer can be the standard sigmoid 
(where the output represents the probability of a test sample being a face). 
The loss you would use would be binary cross-entropy.
With this setup you can imagine having a logistic regression at the last layer of your deep neural net.
