## Key points

- AdaBoost is a boosting algorithm which works by combining the predictions of a sequence of weak learners. These weak learners could be, for example, simple rule of thumbs.

- The algorithm keeps track of a distribution of weights over each $(x_{i},y_{i})$ pairs, and updates this distribution to put more weight on the misclassified examples.

- The final prediction combines the predictions from all the learners in the sequence by taking a weighted majority vote. The weights depend on the error rate of each learner.

- The error is measured with respect to the weight distribution on which the weak learner was trained.

- The algorithm will theoretically overfit if the sequence is too long. However, in practice, the generalization error can sometimes decrease even after the training error has stopped decreasing.