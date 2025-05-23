# Implementing from 00-is-it-a-bird-creating-a-model-from-your-own-data.ipynb from fastai/course22

## First run
The first task once the dev container was up and running was to try out the *00-is-it-a-bird-creating-a-model-from-your-own-data.ipynb* notebook from fastai/course22. This seemed a simple enough task, and was quite simple upon my first run through. I successfully imported the libraries, downloaded the images through a duckduckgo search using the `search_images_ddg` function, and trained a model on the images using all steps in the notebook.


## Analysing performance
From here, the task was to first test this on cpu and then on gpu, using charts such as `nvtop` and `btop` to analyse the difference in both runtime and load when training using a variety of batch sizes.

This was set up using a very simple version of the is-it-a-bird project, where once the images were downloaded the only cells that remained were the initial imports, a function that ran the training on a batch size as a parameter and small cells that ran the individual tests. The first tests were run on GPU as this was the first container I built, and this ran successfully the first time, where nvtop charts were gathered along with the execution time for each test.

After this, CPU graphs were attempted to be created. Most likely due to a Ubuntu update or some docker error, but after many attempts to install it was unable to add as a command, or other relevant charts such as btop.

![](/images/nvtop.png)

Because of this, htop was used to get the instantaneous cpu usage. While not an ideal solution, this worked to show the peak values for the batch training.
From this, results were remembered and compared to the gpu graph as descriptions more than directly as charts.


## Training a model on different images

The next task was to train a model that can recognise multiple classes of images as one trained model. Starting from the original *00-is-it-a-bird-creating-a-model-from-your-own-data.ipynb* model, I first tested using different types of bears following a lecture from ELEC4630. To do this, I changed the search terms to get grizzly, black and teddy bears from a Duckduckgosearch. During this I learned that it is important to put thought into the search terms used, as I ended up training my model on images using the terms 'black', 'grizzly', and 'teddy', which came up with images like these:

![](/images/bears.jpg)

Which as can be seen from images such as the tortoise in a suit(?) that these are largely not relevant images to train on.
After correcting this and getting the tests to work, the classes were changed to the required ones with 'bird', 'cat', 'dog', 'airplane', and 'automobile'. However, while attempting this I encountered an issue several times on the line: `download_images(dest, urls=search_images(f'{o} photo'))` where I would get a 403 error, meaning my IP was likely blocked from too many searches. This did hold up progress as i was unable to work around this for a few days, but eventually was able to search again. Once the images were downloaded, I could once again train the model. From here finishing the training was simple, and the task was completed.
Overall, i learned from this that using remote locations such as dev-containers can be quite difficult when files need to be moved around due to errors, and that it should always be assumed that these errors will occur.