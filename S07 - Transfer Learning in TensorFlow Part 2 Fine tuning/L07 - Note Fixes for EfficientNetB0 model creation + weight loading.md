Hi there!
You're about to harness the power of transfer learning for the Food Vision project!
This note is a quick heads up on some errors you may face in future videos.
The main one being: `tf.keras.applications.EfficientNetB0` producing errors.
I won't get into the details here (they're in the write-up linked below) but these errors have been notorious across different versions of TensorFlow.
Not to worry, there's a one-line fix.
**New:**
base_model = tf.keras.applications.efficientnet_v2.EfficientNetV2B0(include_top=False)
**Old:**
base_model = tf.keras.applications.EfficientNetB0(include_top=False)
This uses the newer version of EfficientNet and is far less prone to bugs.
So if you find yourself getting issues in the following videos, remember to change that old line above to the new line.
I've updated the following resources to discuss all the changes:
- [Full write-up on course GitHub with Notebook 05 changes and details](https://github.com/mrdbourke/tensorflow-deep-learning/discussions/575)
- [Notebook 05 reference on GitHub](https://github.com/mrdbourke/tensorflow-deep-learning/blob/main/05_transfer_learning_in_tensorflow_part_2_fine_tuning.ipynb) (this notebook has the updated and working code)Let me know on Discord or the course [GitHub Discussions](https://github.com/mrdbourke/tensorflow-deep-learning/discussions) if you have any questions!
