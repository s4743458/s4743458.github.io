# My experience with Fingerprint Identification


## Simple Fingerprint Recognition Example.ipynb
before starting to work on the fingerprint task, I tested out running the code from `Simple Fingerprint Recognition Example.ipynb`. This ran fairly smoothly, and gave me a good idea of what is required for fingerprint comparison. This code was implemented into two functions in my code. The first onh would get the local distances, minutiae, and the fingerprint file from the image, and the second would compare fingerprints using these characteristics and return a similarity score.


## The task and starting out with a GUI
The task to complete fingerprint recognition involved the creation of a GUI and template
file/database to:
a. Enroll a fingerprint and associate a name. Store the template in a file or
database
b. Compare a new fingerprint to the fingerprints in the gallery
c. Evaluate your system on several fingerprints and adjust the threshold for
good performance with low error rates
d. Produce a ROC curve showing error rates versus threshold
e. Estimate the false positive rate (false alarm rate) for a false negative rate of 1%

From my previous experience with courses such as CSSE1001 and ENGG2800, I decided to use TKinter to make my GUI. While there are much easier gui libraries out there, I only wanted a couple of buttons and windows, with a filedialog for handling the database. This was done, and worked well enough to compare a fingerprint with the other ones in the database. 

## Mistakes and Statistics
trying to continue from here proved difficult for a couple reasons. Firstly, many of the next steps required rates of error for general comparisons, which from the way my code had been structured would take 80 runs of the comparison button and about 2 hours to run. The first thing i tried was to add a list of thresholds to test multiple at the same time rather than individually gathering values, which took the entire runtime of the comparisons each time, getting minutiae values for each print along the way. This worked for speeding up the threshold testing slightly but the system had to be overhauled for gathering error rates and creating an ROC.

This involved storing a database of each fingerprints information rather than the file itself to save on computation time, and changing the compare button to check every fingerprint against each other fingerprint, resulting in 6400 comparisons. This was then used to get summarised data for error rates, and to produce an averaged ROC.

Through making these many edits I have a few things i could have improved on to make the process smoother. First as this was done in one file it got messy quickly and had issues with getting the various goals done while using a GUI that was still designed for indivudial fingerprint recognition. The GUI could have either been designed with a analysis mode, or simply a seperate section of functions for gathering statistics should have been used.

Overall, I have gained a new respect for the accuracy of modern fingerprint regocnition algorithms, as the sample set was all fairly high quality images returning an average accuracy still around 76%, not near enough for any real world use.