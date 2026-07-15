In November 2021, TensorFlow released [TensorFlow 2.7.0](https://github.com/tensorflow/tensorflow/releases/tag/v2.7.0).
It's now the default version of TensorFlow in Google Colab.
And you might find it breaks the code that's running in the upcoming lectures.
No worries though.
We can fix it.
#### ErrorYou might see this error:
ValueError: Exception encountered when calling layer "sequential" (type Sequential).
    
    Input 0 of layer "dense" is incompatible with the layer: expected min_ndim=2, found ndim=1. Full shape received: (None,)
    
    Call arguments received:
      • inputs=tf.Tensor(shape=(None,), dtype=float32)
      • training=True
      • mask=None
This happens because `model.fit()` no longer automatically upscales inputs from shape `(batch_size, )` to `(batch_size, 1)`.
This results in a **shape error** (remember one of most common errors in deep learning is input and output shapes).
To fix this, you can update the shape.
#### FixIf you're running TensorFlow 2.7.0+ and you're passing a vector to a model, you need to expand its dimensions.
## OLD
# Fit the model
model.fit(X, y, epochs=5) # this will break with TensorFlow 2.7.0+

## New
# Fit the model
model.fit(tf.expand_dims(X, axis=-1), y, epochs=5) # <- updated line
The code adds an extra dimension to `X` on the last axis, turning it `ndim=1` to `ndim=2` (what the model requires).
To see a full explanation of this refer to the following:
- [Discussion on course GitHub](https://github.com/mrdbourke/tensorflow-deep-learning/discussions/256#discussioncomment-1618168)
- [Code example on Google Colab](https://colab.research.google.com/drive/1i4i5wtC50p_FDdKXTWfNpX165I9dbw91?usp=sharing)Notebook [00_neural_network_regression_in_tensorflow.ipynb](https://github.com/mrdbourke/tensorflow-deep-learning/blob/main/01_neural_network_regression_in_tensorflow.ipynb) has also been updated on the course GitHub to reflect these changes.
