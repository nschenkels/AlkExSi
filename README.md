# AlkExSi

## Software requirements to run the model:
The code is written in a Jupyter notebook using Python 2.7. Python can be downloaded from https://www.python.org/ or using Anaconda (recommended for Windows) from https://www.anaconda.com/download/. For installing the Jupyter notebook package, see https://jupyter.org/install. Documentation on how to use the notebook can be found at https://jupyter-notebook.readthedocs.io/en/stable/notebook.html.

## Files and data input:
The main file is 'SiAl_analysis.ipynb', which uses functions from 'SiAl_functions.ipynb'. The code assumes that both are in the same directory, but this can be edited in cell [1] (see below 'Changing parameters') on 'SiAl_analysis.ipynb' file.

The data is read using the Pandas package. The path to the data file should be specified in cell [3]. We assume the data is given in a .csv file with three columns (time, Si measurements and Al measurements) and that the first row contains the names for the columns.  An example of a data set can be found in 'example_data.csv'.

## Brief overview of the method:
There are three different models, depending on how many exponentially decaying terms are considerd (model 1, 2 or 3; with 1, 2 or 3 dacaying fractions respectively). Based on a least squares fit of the first and final part of the data, an initial estimate of the solution is made for model 1. In order to find the optimal set of parameters, a Monte Carlo simulation is performed, where the result of the previous model is expanded and used as a starting point for models 2 and 3. Based on the results of an Akaike and F-test, the best model is selected.

In order to find confidence intervals for each parameter, another experiment is performed ("simulation"). Using a subset of the data and starting from the parameters found with the Monte Carlo method, a local optimization procedure is run to find the new optimal set of parameters for the subset of the data. By doing this many times, we can find confidence intervals for the parameters.

## Changing Input parameters:
A brief overview of the parameters that can be changed and where to find them is given here: (the cell number (between square brackets) corresponds to the number starting from a restarted notebook). Specific lines to change in the cell are detailed in the script.
- [1] The path to 'SiAl_functions.ipynb' can be changed here.
- [2] The filename of the datafile and its path can be changed here.
- [3] If the datafile is of a different format, adjustments need to be made here.
- [4] For an initial estimate of the parameters, data corresponding to the first and last 10 minutes of the measurements are selected. This time window can be changed here.
- [6], [7], [8] The number of times the Monte Carlo simulation is run and the number of samples drawn per run can be changed.
- [11] The size of the random subsets and the number of times a new subset is drawn for the second part of the analysis (simulation) can be changed here. The amount of noise added can also be changed here.
- [12] The parameters can be sorted by the largest value of k, AlkExSi or SiAl. This can be changed by replacing the function 'Sort_By_*'. To be applied in case k values (default sort value) of two fractions overlap.

## Output:
The most important results of the analysis can be found in the following cells: (the cell number (between square brackets) corresponds to the number starting from a restarted notebook)
- cell [9] lists the results of the Monte Carlo simulations for the three models.
- cell [10] lists the results of the model selected by the Akaike test.
- cell [12] lists the confidence intervals found after the analysis.



