The old README is (modified) below. Special thanks to the DGCNN group and paper that our project was based on. 

To run the code please see below. (Run make in lib/ and then you can run ./run_DGCNN.sh or ./grid_search.sh). The values in these 2 scripts are modified based on which experiment we are doing. We also name the experiment based on the variable in main.py "testname". For grid search, we use the parameters as the name. Otherwise, we write our own custom testname. To change the embedding, we can change sortpooling_k in the shell scripts or CONV_SIZE. And to add more layers to the CNN, we can uncomment the code  e.g. adding the the 1.5 layer in between layer 1 and 2. 

We leave our important results in the results folder. See our grid search results and other named results that we used in our final report. 

PyTorch DGCNN
=============

About
-----

PyTorch implementation of DGCNN (Deep Graph Convolutional Neural Network). Check https://github.com/muhanzhang/DGCNN for more information.

Requirements: python 2.7 or python 3.6; pytorch >= 0.4.0

Installation
------------

This implementation is based on Hanjun Dai's structure2vec graph backend. Under the "lib/" directory, type

    make -j4

to compile the necessary c++ files.

-----------------------------------------------------------------------
-----------------------------------------------------------------------
For Data Mining Final Project CS247 results, Spring 2021:

Under the root directory of this repository, type

    ./grid_search.sh

to run DGCNN on the default dataset MUTAG and generate plots and results for the grid search on dropout, hidden layers, and optimizers.

-----------------------------------------------------------------------
-----------------------------------------------------------------------

Or type 

    ./run_DGCNN.sh DATANAME FOLD

to run on dataset = DATANAME using fold number = FOLD (1-10, corresponds to which fold to use as test data in the cross-validation experiments).

If you set FOLD = 0, e.g., typing "./run_DGCNN.sh DD 0", then it will run 10-fold cross validation on DD and report the average accuracy.

Alternatively, type

    ./run_DGCNN.sh DATANAME 1 200

to use the last 200 graphs in the dataset as testing graphs. The fold number 1 will be ignored.

Check "run_DGCNN.sh" for more options.

Datasets
--------

Default graph datasets are stored in "data/DSName/DSName.txt". Check the "data/README.md" for the format. 

In addition to the support of discrete node labels (tags), DGCNN now supports multi-dimensional continuous node features. One example dataset with continuous node features is "Synthie". Check "data/Synthie/Synthie.txt" for the format. 

There are two preprocessing scripts in MATLAB: "mat2txt.m" transforms .mat graphs (from Weisfeiler-Lehman Graph Kernel Toolbox), "dortmund2txt.m" transforms graph benchmark datasets downloaded from https://ls11-www.cs.tu-dortmund.de/staff/morris/graphkerneldatasets

How to use your own data
------------------------

The first step is to transform your graphs to the format described in "data/README.md". You should put your testing graphs at the end of the file. Then, there is an option -test_number X, which enables using the last X graphs from the file as testing graphs. You may also pass X as the third argument to "run_DGCNN.sh" by

    ./run_DGCNN.sh DATANAME 1 X

where the fold number 1 will be ignored.

Reference
---------

If you find the code useful, please cite our paper:

    @inproceedings{zhang2018end,
      title={An End-to-End Deep Learning Architecture for Graph Classification.},
      author={Zhang, Muhan and Cui, Zhicheng and Neumann, Marion and Chen, Yixin},
      booktitle={AAAI},
      year={2018}
    }

Muhan Zhang, muhan@wustl.edu
3/19/2018
