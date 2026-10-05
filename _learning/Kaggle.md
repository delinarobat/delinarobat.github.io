---
layout: page
title: Kaggle Machine Learning Courses
description: Notes from three Kaggle courses (Intro to ML, Intermediate ML, and Feature Engineering) on how a tabular machine learning workflow fits together
img: /assets/img/kaggle-logo.png
importance: 4
category: Learning
---

## What Does a Tabular Machine Learning Workflow Look Like, Start to Finish?

**Self-directed learning project**  
**May to July 2026**  
**Tools: Python · pandas · scikit-learn · XGBoost · Kaggle Learn**

Notes from three Kaggle courses taken in sequence: Intro to Machine Learning, Intermediate Machine Learning, and Feature Engineering.

## Why I Started

I wanted to understand how machine learning works before using it on construction and BIM data. Rather than jumping straight into a complex model, I chose Kaggle's short, hands-on courses to learn the full workflow in order: building a model, handling messy data, and improving the inputs.

## Course 1: Intro to Machine Learning

The basics: loading data with pandas, building a decision tree, validating a model on held-out data, and recognizing underfitting and overfitting. The course ends with random forests.

**Key takeaway:** a model that scores well on the data it was trained on can still fail on new data, so validation is not optional.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/delina_robat_-_Intro_to_Machine_Learning.png" title="Intro to Machine Learning certificate" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Certificate of completion for Kaggle's Intro to Machine Learning (May 2026).
</div>

## Course 2: Intermediate Machine Learning

The practical problems of real datasets: missing values, categorical variables, pipelines, cross-validation, gradient boosting with XGBoost, and data leakage.

**Key takeaway:** pipelines keep preprocessing consistent, and leakage can make results look better than they really are.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/delina_robat_-_Intermediate_Machine_Learning.png" title="Intermediate Machine Learning certificate" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Certificate of completion for Kaggle's Intermediate Machine Learning (June 2026).
</div>

## Course 3: Feature Engineering

How to improve a model by improving its inputs: mutual information to find useful features, creating new features, clustering, PCA, and target encoding.

**Key takeaway:** better features can matter more than a fancier model.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/delina_robat_-_Feature_Engineering.png" title="Feature Engineering certificate" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Certificate of completion for Kaggle's Feature Engineering (July 2026).
</div>

## What I Learned

* A good score means little unless the model is validated on data it has not seen, and cross-validation gives a more trustworthy estimate than a single split.
* Most of the work is not the model itself but preparing the data: missing values, categories, and consistent preprocessing.
* Data leakage is easy to introduce by accident and can make a weak model look strong.
* Creating better features can improve results more than switching to a more complex algorithm.

## Limitations

These are guided courses with clean, prepared datasets. They taught me the workflow, but a certificate shows I completed the material, not that I can handle messy real-world data. I started applying these ideas in my [BIM Issue Text Classification](/learning/Reading BIM Issues with NLP)project.

### Skills

`Python` · `pandas` · `scikit-learn` · `XGBoost` · `Feature Engineering` · `Machine Learning`
