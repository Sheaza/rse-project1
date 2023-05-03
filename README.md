# Project 1 -  Content-based recommender

### Project description
<p>The aim of this project was to create a content-based recommender based on real hotel data.</p>

## Data preprocessing

#### data_preparation file
<p>In this file I've done basic data preprocessing and filtering of raw data as well as aggregation of certain features into buckets. </p>

#### recommender_and_evaluation file

<p>As a base there is 6 <strong>categorical</strong> columns: <br>

    ['term', 'length_of_stay_bucket', 'rate_plan', 'room_segment', 'n_people_bucket', 'weekend_stay']

<p>For each user and item I extracted the most common label in every feature on which I later used one hot encoding getting 24 separate features. </p>

## Recommender testing and tuning

<p>After some manual tests I've decided to use <strong>SVG-based</strong> recommender because it was giving most promising results.</p>

<p>While tuning I've decided to use only 1000 samples from original dataset because it was very time-consuming. I've initialized parameters space as below:</p>

    param_space = {
    'n_neg_per_pos': hp.quniform('n_neg_per_pos', 1, 10, 1),
    'C': hp.loguniform('C', -7, 0)
    }
<p>And here are the results of this tuning:</p>


![SVG tuning results](./Zrzut ekranu 2023-05-03 201649.png?raw=true "SVG tuning results")


<p>At the end I've used smaller C value based on personal experience, but I've also noticed from tuning that n_neg_per_pos parameter works best when 10.</p>

## Results compared to Amazon Recommender
<p>I've used C value of 10e-6 and n_neg_per_pos equals to 10.</p>
<strong>(I forgot to change recommender name..)</strong>

![SVG tuning results](./img.png?raw=true "SVG tuning results")

### Requirements to run
<pre>
- Python 3.8
- pip install -r requirements.txt
</pre>
