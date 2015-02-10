SegEM: Semi automated image analysis toolkit for Connectomics
========================================

Usage
---------

Just provide requested information on top of initalSettings.m
Required information:
+ dataDirectory = Location of data acquired via segem.io or currently pointer to Frankfurt Fileserver under \\storage.hest.corp.brain.mpg.de\Data\Data\berningm\20150205paper1submission\
+ jobManagerName = Name of working Matlab Jobmanager profile
+ outputDirectory = Directory to store data and figures generated by scripts

Next start Matlab with the working directory set to the root folder of this code repositorium and run initalSettings.m
This will prompt you to choose whether you want to work with retina or cortex (version of code and data)
IMPORTNAT NOTE: So far only cortex is set up and tested, will remove this when retina is finished

This will open relevant scipts which can be executed from top to bottom using Ctrl+Enter and are open in a sequential order that should be most instructive to follow (e.g. start with top- or leftmost script)
See “Cell Mode” in Matlab help for more information on using Ctrl + Enter for executing a cell (=between line starting with %%)

The most important parts of the code for CORTEX are (always including some visualization):
+ cnnStart: load training data, train a convolutional neuronal network, paralell network training
+ cnnParameterSelection: Automated hyperparameter selection and variation of learning rates for each layer
+ mainSegCortex: steps from classification result by CNN to segmentation (grid parameter search for watershed segmentation) including skeleton based split-merger metrics
+ bigFwdPassStart: Apply learned CNN classifier (learned in point 1) and watershed segmentation steps (with parameters optimized in 2)
+ skeletonBasedCortex: Use segmentation of whole dataset (point 4 in this list) to use skeleton reconstructions for volume reconstructions or contact detection between cell pairs (a segmentation is also provided because step 4 is computationally expensive)

The most important parts of the code for RETINA are:
TO DO
