---
layout: page
title: Mapping LEED v5 to BIM
description: An interactive reference that classifies all 49 LEED v5 BD+C New Construction requirements by how far they can be computed from a BIM model, whether they are geometric, and which project phase they belong to
img: /assets/img/leed-overview.png
importance: 4
category: Learning
---

## Mapping LEED v5 to BIM

**Self-directed learning project**  
**Summer and Autumn 2026**  
**Tools: Revit 2025 · Dynamo 3.0.3 · IFC · Shared Parameters · HTML**

I am working on an article that connects LEED v5 sustainability requirements to BIM. Before calculating anything, I needed to know where to focus: which requirements can realistically be computed from a Revit model, which depend on information the model does not contain, and how each one could be approached.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/leed-overview.png" title="The LEED v5 to BIM computational assessment framework" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    The dashboard, showing the LEED v5 BD+C New Construction requirements as cards, with filters on the left.
</div>

## Why I Built It

After months of reading about LEED v5 and about what automation can and cannot do, I had a lot of notes and no clear way to compare them. I wanted every requirement classified in the same way, so I could decide where to start. I built an interactive HTML dashboard for this, with help from Claude.

## The Questions It Answers

For each of the 49 requirements, the dashboard records:

* **Is it geometric?** Yes, partial, or no: can it be derived from the model's geometry (areas, distances, counts), or does it depend on product data, documents, or operational records?
* **Which phase does it start in?** Design, construction, or occupancy, or a combination.
* **How computable is it?** A computational level from 0 to 6, plus a classification (A to H) describing the approach, such as Dynamo with shared parameters.
* **Can compliance be proven with that computation?** Yes, partial, or no. Computing a number is not the same as being able to prove LEED compliance with it.

## Filtering to Find the Priorities

The filters can be combined. For example, selecting **Geometric: Yes** and **Earliest phase: Design** narrows the list to 8 requirements, such as Heat Island Reduction, Light Pollution Reduction, and Low-Emitting Materials. These are the best candidates to automate first.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/leed-filtered.png" title="The dashboard after filtering" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    The dashboard filtered to geometric requirements that start in the design phase.
</div>

## Looking at One Requirement in Detail

Clicking a card opens a detail view. For **SSc6, Light Pollution Reduction**, it shows the required inputs (lighting zone, luminaire schedule, glare ratings, distances to the lighting boundary), whether the metric can be computed, and whether LEED compliance can be proven with it. Here the answer to both is yes, but only once the luminaire rating data from manufacturers has been added as shared parameters. This is a good example of a requirement that looks purely geometric but still needs product data.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/leed-detail.png" title="Detail view of SSc6, Light Pollution Reduction" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    The detail view for SSc6, Light Pollution Reduction.
</div>
## What I Learned

When a problem has many criteria, it quickly becomes complex, and classification helps a lot to keep moving forward. The most important step is to understand the parameters and the goal first. Only then can I define meaningful criteria and use them to sort everything.

## Limitations and Next Steps

The dashboard is a work in progress. The requirement hierarchy and the feasibility classification are complete, but the per-variable formulas, working Dynamo graphs, and IFC and API workflows are not built yet. Where a requirement would eventually carry a full workflow, the dashboard shows the classification and key inputs instead of inventing one. The classification also reflects my own reading and judgment and has not yet been validated on real models. The next step is to build the calculations, starting with the requirements the filters flagged as the best candidates.

### Role

`LEED v5` · `BIM` · `Revit` · `Dynamo` · `IFC` · `Sustainability` · `Automation`
