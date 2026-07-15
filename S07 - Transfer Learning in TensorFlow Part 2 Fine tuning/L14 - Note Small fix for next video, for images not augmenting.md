Hello hello!
Before you jump into the next video, there's something small to note with the data augmentation model we build.
Some people have had the issue of images not augmenting (augmentation involves slightly changing an image, this will be covered in more detail in the video) in notebook 05.
You can see the issue on the course GitHub here: [https://github.com/mrdbourke/tensorflow-deep-learning/issues/350](https://github.com/mrdbourke/tensorflow-deep-learning/issues/350)
This is because of a recent update to how augmentation layers work in TensorFlow 2.8.
A fix should be on the way from the TensorFlow team but for now, one way to fix it is to make sure the parameter `training=True` is passed to a data augmentation model.
This is because data augmentation is only intended to work during _training_ and not testing.
#### Code beforeThis code appears at 5:46 in the next video.
`augmented_img = data_augmentation(img)`
Doing this would result in images sometimes _not_ being augmented (changed).
#### Code after the fix`augmented_img = data_augmentation(img, training=True)`
You should see your images slightly change after running this line (as well as the rest of the code in the video).
There's an [example notebook available here](https://colab.research.google.com/drive/1qhCnJZgYAPzSnjq-PhB4fM5CtvqS34UP?usp=sharing) to see this in action.
#### Still have issues?If you're still having issues, please see the discussion for this issue on the course GitHub: [https://github.com/mrdbourke/tensorflow-deep-learning/discussions/369](https://github.com/mrdbourke/tensorflow-deep-learning/discussions/369)
Happy augmenting!
