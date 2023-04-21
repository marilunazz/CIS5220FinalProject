# CIS5220FinalProject
Our project aims to enhance the user experience on StackOverflow by suggesting relevant, previously answered posts for newly posted questions. Our model will utilize similarity scores and answer quality metrics to provide links to StackOverflow posts that could potentially answer or provide valuable insights for the new question.

## Pre-Processing
Data cleaning and pre-processing can be found on the 'Preprocessing.ipynb'.

## Baselines
Our baselines can be found on the 'Baselines.ipynb'. The data to run this can be found on 'samples_df.pkl', and the output of this notebook is stored in 'data_both_baselines_sample.pkl'.

## Model
Our project modifes BERT. We add a combining module that takes the outputs of BERT in addition to categorical and numerical features to produce rich multimodal features for downstream classification/regression layers. Given a pretrained transformer, the parameters of the combining module and transformer are trained based on the supervised task. We followed the following code to achieve our model: https://github.com/georgian-io/Multimodal-Toolkit.

