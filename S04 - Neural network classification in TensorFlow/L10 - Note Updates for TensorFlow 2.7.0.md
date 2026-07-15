A quick note on the next couple of videos.
If you're using TensorFlow 2.7.0+ (default in Google Colab from November 2021), you might run into some shape errors when trying to fit a model (calling `model.fit()`).
This happened due to some changes in TensorFlow 2.7.0.
In short, TensorFlow no longer automatically upranks single dimension data from `(batch_size, )` to `(batch_size, 1)`.
This is fine because it can be fixed with a couple of lines of code.
#### ErrorYou might see this error when trying to fit `model_3` :
ValueError: Exception encountered when calling layer "sequential_2" (type Sequential).
Input 0 of layer "dense" is incompatible with the layer: expected min_ndim=2, found ndim=1. Full shape received: (None,)
This is a shape error, one of the most common in deep learning and you should expect to get more of them.
#### Fix (for next video)To fix this, when creating the `model_3`, define the `input_shape` parameter of the first layer (this tells the model what shape of the data it should be expecting.
# Set random seed
tf.random.set_seed(42)

# 1. Create the model (this time 3 layers)
model_3 = tf.keras.Sequential([
  ## Before TensorFlow 2.7.0
  # tf.keras.layers.Dense(100), # add 100 dense neurons

  ## After TensorFlow 2.7.0
  tf.keras.layers.Dense(100, input_shape=(None, 1)), # <- define input_shape here
  tf.keras.layers.Dense(10), # add another layer with 10 neurons
  tf.keras.layers.Dense(1)
])

# 2. Compile the model
model_3.compile(loss=tf.keras.losses.BinaryCrossentropy(),
                optimizer=tf.keras.optimizers.Adam(), # use Adam instead of SGD
                metrics=['accuracy'])
And then when fitting the model, expand the dimensions of the input data.
# Set random seed
tf.random.set_seed(42)

# Create some regression data
X_regression = np.arange(0, 1000, 5)
y_regression = np.arange(100, 1100, 5)

# Split it into training and test sets
X_reg_train = X_regression[:150]
X_reg_test = X_regression[150:]
y_reg_train = y_regression[:150]
y_reg_test = y_regression[150:]

# Fit our model to the data

## Note: Before TensorFlow 2.7.0, this line would work
# model_3.fit(X_reg_train, y_reg_train, epochs=100) # <- this will error in TensorFlow 2.7.0+

## After TensorFlow 2.7.0
model_3.fit(tf.expand_dims(X_reg_train, axis=-1), # <- expand input dimensions
            y_reg_train,
            epochs=100)
These two fixes should get your model working as usual.
#### ResourcesNotebook 02 on GitHub has been updated to reflect these changes. And a note has been added to the next video as a reminder.
- [Notebook 02](https://github.com/mrdbourke/tensorflow-deep-learning/blob/main/02_neural_network_classification_in_tensorflow.ipynb) (working code)
- [GitHub Discussion talking about the issue](https://github.com/mrdbourke/tensorflow-deep-learning/discussions/278) (if you have more questions, post them here)
- [Example Colab notebook with the isolated issue and fixes](https://colab.research.google.com/drive/1_dlrB_DJOBS9c9foYJs49I0YwN7LTakl?usp=sharing)
