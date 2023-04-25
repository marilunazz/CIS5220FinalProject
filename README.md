# CIS5220FinalProject
## Team - The Dialogue Dominators
Our project aims to enhance the user experience on StackOverflow by suggesting relevant, previously answered posts for newly posted questions. Our model will utilize similarity scores and answer quality metrics to provide links to StackOverflow posts that could potentially answer or provide valuable insights for the new question.

## Our data
Our dataset contains the best questions from Stack Overflow database from 2009-2022. We have ~100k posts. Each data point includes a total of 9 fields: post Id, CreationDate, Title, Body, Tags, ViewCount, CommentCount, AnswerCount, Score. Better posts will improve our model as the data we train it on will have relevant information and appropriate answers.
https://www.kaggle.com/datasets/michaelfumery/stackoverflow-questions-filtered-2011-2021?select=StackOverflow_questions_2009.csv

A sample Id, Title and Body is as follows:

Title: why does the sqlserver optimizer get so confused with parameters?

Body: i know this has something to do with parameter sniffing, but i am just perplexed at how something like the following example is even possible with a piece of technology that does so many complex things well.  many of us have run into stored procedures that intermittently run several of orders of magnitude slower than usual, and then if you copy out the sql from the procedure and use the same parameter values in a separate query window, it runs as fast as usual.  i just fixed a procedure like that by converting this:  alter procedure p_myproc (     @param1 int ) as -- do a complex query with @param1   to this:  alter procedure p_myproc (     @param1 int ) as  declare @param1copy int; set @param1copy = @param1;  -- do the query using @param1copy   it went from running in over a minute back down to under one second, like it usually runs.  this behavior seems totally random.  for 9 out of 10 @param1 inputs, the query is fast, regardless of how much data it ends up needing to crunch, or how big the result set it.  but for that 1 out of 10, it just gets lost.  and the fix is to replace an int with the same int in the query?  it makes no sense.  [edit]  @gbn linked to this question, which details a similar problem:    i hesitate to cry "bug!" because that is so often a cop-out, but this really does seem like a bug to me.  when i run the two versions of my stored procedure with the same input, i see identical query plans.  the only difference is that the original takes more than a minute to run, and the version with the goofy parameter copying runs instantly.

## Pre-Processing
Data cleaning and pre-processing can be found on the 'Preprocessing.ipynb'.

## Baselines
Our baselines can be found on the 'Baselines.ipynb'. The data to run this can be found on 'samples_df.pkl', and the output of this notebook is stored in 'data_both_baselines_sample.pkl'.

## Model
We have fine tuned a pre-trained BERT model on Stack Overflow posts. This variant of BERT has 12 transformer layers and 110m parameters. We have fine tuned our pre-trained BERT model for our ChatGBT-labeled STS-B (Semantic Textual Similarity Benchmark) data, which involves predicting the degree of semantic similarity between two sentences on a scale of 0 to 10. Once our model has been fine-tuned, we test different sets of training parameters and begin training. We now test our model using various loss statistics. This can be found on 'Bert522.ipynb' and the data to run this notebook can be found with 'bert_data.csv'. 

## Results
The code for the results can be found in the last section of 'Bert522.ipynb', and the data to run this 'data_both_baselines_sample.pkl'. The scores generated were saved in 'scores.pkl'.

