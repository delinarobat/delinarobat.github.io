---
layout: page
title: BIM Issue Text Classification
description: An exploratory NLP prototype that classifies BIM design-coordination issues by responsible discipline and severity, built to learn how far a simple model can go on tracker-style text
img: /assets/img/nlp-cm-severity.png
importance: 2
category: Learning
---

## Can We Classify BIM Coordination Issues from Text Alone?

**Self-directed learning project**  
**October 2026**  
**Tools: Python · scikit-learn · Jupyter**

An exploratory prototype inspired by a future-work idea in recent cloud-BIM research.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/nlp-cm-severity.png" title="Severity confusion matrices, before and after class weighting" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Severity confusion matrices without (left) and with (right) class weighting.
</div>

## Why I Started

While reading recent research on cloud-based BIM collaboration (Bhonde, Zadeh and Staub-French, *Buildings*, 2026), one idea stood out: tools like Revizto accumulate thousands of text records (issue descriptions, comments, statuses), and that text could be analyzed automatically. I wanted to learn how far a very simple NLP approach could go on this kind of data.

This is a learning exercise, not a replication of that work, and it is not validated on real project data.

## The Data Problem

Real coordination data isn't public, so I generated **205 synthetic issues** with an LLM, in the style of a tracker entry (for example, "Duct vs. sprinkler main, L3, grid C-4"). Each issue is labeled with the **discipline that must resolve it** (HVAC, Plumbing, Electrical, FireProtection) and a **severity level** (Critical, Major, Minor). I defined the severity rules up front: Critical means life-safety or code violation, Major means high cost or schedule impact, and Minor means a small, easy fix.

The main limitation is that synthetic data is cleaner than real data.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/nlp-data.png" title="Loading the dataset" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    The dataset: 205 issues, balanced across disciplines.
</div>

## A Deliberately Simple Model

I used TF-IDF plus logistic regression, with no deep learning. A simple baseline tells you what the data itself can support.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/nlp-model.png" title="The model and its evaluation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    The model pipeline and its classification report.
</div>

## First Surprise: Discipline Is Ambiguous

On a single 41-row test split, discipline accuracy was only **0.56**; 5-fold cross-validation gave **0.78**. The confusion matrix showed why: HVAC and FireProtection were mixed up. A clash like "duct vs. sprinkler" mentions both systems, but the label is *who must fix it*, and that can't be read from keywords alone.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/nlp-cm-discipline.png" title="Discipline confusion matrix" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Discipline confusion matrix on the test split.
</div>

## Second Surprise: The Costliest Class Was the Hardest

For severity, overall accuracy looked fine (0.78), but recall on **Critical** (life-safety) issues was only **0.25**. In construction, missing a Critical issue is the most expensive mistake. Adding class weighting raised Critical recall to **0.75** at the cost of a few false alarms, a trade-off that is usually worth it in safety contexts. With only 8 Critical test rows, this is a signal rather than proof.

## Stress Test: A Different Writing Style

To check whether the model just learned the style of my synthetic data, I wrote 24 new issues in a terser, abbreviation-heavy style (with help from an AI assistant; the labels are my own and debatable in places). Accuracy dropped: discipline from 0.78 to 0.67, and severity from 0.85 to 0.67-0.75. Class weighting, which helped on the original data, did not clearly help here. With only 24 samples, I treat this as a signal, not a result.

## What I Learned

* High accuracy on synthetic data says little; testing on a different style says more.
* Labels like "who resolves this" are partly organizational, not purely textual, which connects to the paper's point about needing shared definitions (for example, of issue priority).
* Overall accuracy can hide failure on the class that matters most.

## Limitations and Next Steps

The data is synthetic, small, and single-label, and the stress-test labels are subjective. Next steps would be real anonymized issue data, multi-label classification (many clashes involve two disciplines), sentence embeddings, and shared severity guidelines for annotation.

### Role

`NLP` · `Python` · `scikit-learn` · `BIM` · `Text Classification` · `Design Coordination`
