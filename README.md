[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/research-reuse/rpt-project/master?filepath=rpt-project.ipynb)

## Introduction

This repository has been forked from <https://github.com/ScholCommLab/rpt-project> to be used as a research reproducibility exemplar for the [Curating Data Sets for Reproducibility](https://research-reuse.github.io/) workshop at the [Canadian Data Curation Forum](https://data-curation.github.io/), held on October 16-18, 2019 in Hamilton, ON.

While we have tried to change as little as possible, there were things that needed to be fixed in order to have the project run in [MyBinder](https://mybinder.org/). A folder called [binder](https://github.com/research-reuse/rpt-project/tree/master/binder) was added to hold the files required for the MyBinder implementation. These are the configuration files that allow the [PISA Jupyter notebook file] (https://github.com/research-reuse/rpt-project/blob/master/rpt-project.ipynb) to be packaged as a container file. The first file `requirements.txt` is a dependencies file, listing all of the Python modules that are required to run the code. The second file `runtime.txt` specifies which Python version was used to write the code.

In order for this code to run in MyBinder, we needed to download the data from the [project Dataverse repository](https://doi.org/10.7910/DVN/VY4TJE) and place it in a directory in this repository. This required changing the file paths in the notebook. In addition, the file name used in the original notebook did not match the filename of the data file in Dataverse, so this required changing too. The filename was changed from `RPT_final_dataset.csv` to `dataverse-files/scholcommlab-rpt-master-april-2019.csv`. 

There is a dependency for this code called `[pyperclip](https://pypi.org/project/pyperclip/)` that we couldn't get to work in the `requirments.txt file`, for this reason, the module is commented out in the first code cell. `pyperclip` is quite complex, and required more than just a module installation, but requires changes to other types of permissions on the user's machine. This module is required for several of the code cells, so in order for the code to partially work, we've commented out all of the code that requires this module. As there are existing comments in the code, our comments are indicated with `###`, rather than `#`.

Finally, the original name of the notebook file was `Analysis of data from the Review, Tenure and Promotion project.ipynb`. This name caused an error in the creation of the MyBinder container (it was likely the comma). For this reason, the filename was changed to `rpt-project.ipynb`. 


### Notes on Dependencies

There are two ways to load Python modules: through an `environment.yml` file (which loads through Anaconda) or through a `requirements.txt` file (which still somehow loads through Conda).

These have different formatting requirements. The tricky part is that it's better if the dependencies file is built with the project, rather than being reconstructed afterwards. This is because some of the modules need to have specific version numbers, and it takes a bit of trying to get those to work after the fact. Determining the specific module versions was time-intensive (and frustrating). 

At the time of file creation, running the following commands would be extremely helpful:
```
IPython.sys_info() # requires importing the IPython module, prints detailed information about the runtime environment
pip freeze > requirements.txt # prints a list of all dependencies, 
                              # refer to https://pip.pypa.io/en/stable/reference/pip_freeze/ for specifics
```

For this project we've used a `requirements.txt file`, which also needs an additional file called `runtime.txt` to specify the Python version. This project was built in Python2.7, which will not be supported as of Jan 2020. Below is a sample set of each file, showing the formatting differences between the two.

#### environment.yml example

```
channels:
  - conda-forge
dependencies:
  - conda==4.7.12
  - python
  - numpy>=1.11
  - pip
  - scipy>=0.18
  - patsy>=0.4.0
  - cython>=0.24
  - pip:
    - wbdata==0.2.7
    - statsmodels.formula.api==0.10
    - pandas>=0.19
    - matplotlib
```

#### requirements.txt example

```
numpy==1.11
scipy==0.18
patsy==0.4.0
cython==0.24
wbdata==0.2.7
pandas==0.19
matplotlib
pycountry
```





# Review, Promotion, and Tenure Project
Code associated with the [Review, Promotion and Tenure project](https://www.scholcommlab.ca/research/rpt-project/). 

This code is used to process the data found here: 

* Alperin, Juan Pablo; Muñoz Nieves, Carol; Schimanski, Lesley; McKiernan, Erin C.; Niles, Meredith T., 2018, "Terms and Concepts found in Tenure and Promotion Guidelines from the US and Canada", [https://doi.org/10.7910/DVN/VY4TJE](https://doi.org/10.7910/DVN/VY4TJE), *Harvard Dataverse*, V2, UNF:6:iLWsin0hJJ2xQU8CI2rqlA== [fileUNF] 

An initial publication can be found here: 

* Alperin, J.P., Muñoz Nieves, C., Schimanski, L., Fischman, G.E., Niles, M.T. & McKiernan, E.C. (2018). How significant are the public dimensions of faculty work in review, promotion, and tenure documents? *Humanities Commons* [preprint]. doi: [10.17613/M6W950N35](https://doi.org/10.17613/M6W950N35)
