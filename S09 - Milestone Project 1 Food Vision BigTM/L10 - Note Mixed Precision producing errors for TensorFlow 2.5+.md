Hey there,
Just putting this note here to let you know that you may face an error in the next video if you're using TensorFlow 2.5+.
**Error**
The error happens when you turn on mixed precision training for EfficientNetBX models (if you're not sure what this is, you'll see it in the next video).
It'll look something like this:
`TypeError: Input 'y' of 'Sub' Op has type float16 that does not match type float32 of argument 'x'`
As of **29 May 2021**it looks like this is a bug in TensorFlow 2.5+.
There is an issue thread tracking the progress of an update on GitHub: [https://github.com/tensorflow/tensorflow/issues/49725](https://github.com/tensorflow/tensorflow/issues/49725)
**How to fix it**
The current workaround is to downgrade to TensorFlow 2.4.1 (the last version before 2.5).
You can do this in Google Colab by running:
# Downgrade Tensorflow Version (run this in Google Colab) 
!pip install tensorflow==2.4.1
After doing so, you'll have to **restart your runtime** (Runtime -> Restart runtime) to ensure TensorFlow 2.4.1 is active.
import tensorflow as tf
tf.__version__
 
>>> '2.4.1'
Once TensorFlow 2.4.1 is installed, the code should work as normal.
Ashik has also posted this on the course GitHub discussions: [https://github.com/mrdbourke/tensorflow-deep-learning/discussions/82](https://github.com/mrdbourke/tensorflow-deep-learning/discussions/82)
If you have any issues, please post your question/reply there so others can see.
If a fix for this issue comes for TensorFlow 2.5+ (it should), we'll update/remove this post.
Happy mixed precision training,
- Daniel
