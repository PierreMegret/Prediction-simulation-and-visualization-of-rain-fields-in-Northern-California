# Prediction, simulation and visualization of rain fields in Northern California
## The project
Rain fields show complex behavior that is difficult to reproduce with physical models while data-driven approach can be beneficial in a number of applications.
Python was the programming language for this project. I implemented a methods from scratch using basic linear algebra tools available in NumPy/SciPy packages.

## The code
The code is organized as a python class with prediction, simulation and visualization functionalities (PierreMegret_Predictor) and an evaluation file (PierreMegret_Evaluation).
## The data
The dataset I used in this project was an hourly rainfall rate in mm/hour measured in California at a given time of a given winter day of 2025. The meteorological sensing network covering California contains 827 sensors. Of all the 827, the measurements in 414 locations were available, my task in Part 1 was to provide a prediction of the hourly rainfall rate for the other 413 locations reserved as test sites.
### Part 1. Predictions
I implemented a Gaussian Process (GP) regression method with an isotropic Gaussian covariance function of a given bandwidth. The class implementing GP contains a function returning a predictive mean. The training dataset and the value of the bandwidth parameter have to be provided by a user.
I trained the model on the training dataset contained and found an optimal value of the bandwidth parameter. I used a computational approach of minimizing the k-fold cross-validation error on the training set.
Then I computed predictions for the locations contained in the file test of 413 locations.
### Part 2. Simulations
I implemented a function returning one conditional stochastic simulation at a set of locations xgrid provided as an argument to the function. The file contained a sample 50x50 grid within the [38.5, 39.3, -119.8, -120.8] bounding box.
### Part 3. Visualization
I implemented a function to visualize one stochastic simulation for the area within the following bounding box: [38.5, 39.3, -119.8, -120.8]. This function produces and writes to disk an image and a ground overlay KML file with a static geo-referenced image of a realization my stochastic simulation.
