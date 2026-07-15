In some of the lectures, you'll notice `.csv` files being imported from file using something like:
`heart_disease = pd.read_csv("data/heart-disease.csv")`
This is helpful if you have the data downloaded to your computer or in the same directory as your notebook.
But if you don't, another great feature of pandas is being able to import `.csv` files directly from a URL.
For example, for the `heart-disease.csv` file, using the `read_csv()` function you can directly import it using the URL [from the course GitHub repo](https://github.com/mrdbourke/zero-to-mastery-ml):
`heart_disease = pd.read_csv("https://raw.githubusercontent.com/mrdbourke/zero-to-mastery-ml/master/data/heart-disease.csv")`
**Note:** If you're using a link from GitHub, make sure it's in the "raw" format, by clicking the raw button.

[1.png](https://uploads.teachablecdn.com/attachments/tsKsfbQnTF677BKS9PEY_1.png)
