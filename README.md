Creating, saving and extracting outputs from custom models with Tensorflow 2.2

This notebook was written along with a medium post to adress some shortcomings of the -otherwise incredible- Tensorflow 2.2 update.

It proposes:

* A CustomModel subclass of tf.keras.Model with custom save/load functions that can save the model in a much more adaptible and generalized way than the default ones.
* A way to overwrite train_step() and make_train_function() so that one can extract variables from the training graph, even in multi-GPU configurations
* Custom Callback functions that work with the aforementioned changes to avoid errors, allow more control over what variables are logged/printed, and use custom checkpoints to resume training after interruptions without issues with model and optimizer weights and without overwritting previous measurements.

The changes make it possible to monitor variables other than metrics during training without having to resort to custom training loops and give up fit's advantages, and also make it much easier to train models in circumstances where interruptions may occur (e.g. in Colab).
