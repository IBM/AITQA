<!-- This should be the location of the title of the repository, normally the short name -->
# AIT-QA: Question Answering Dataset over Complex Tables in the Airline Industry 

<!-- Build Status, is a great thing to have at the top of your repository, it shows that you take your CI/CD as first class citizens -->
<!-- [![Build Status](https://travis-ci.org/jjasghar/ibm-cloud-cli.svg?branch=master)](https://travis-ci.org/jjasghar/ibm-cloud-cli) -->

<!-- Not always needed, but a scope helps the user understand in a short sentance like below, why this repo exists -->
## Abstract

Recent advances in transformers have enabled Table Question Answering (Table QA) systems to achieve high accuracy and SOTA results on open domain datasets like WikiTableQuestions and WikiSQL. Such transformers are frequently pre-trained on open-domain content such as Wikipedia, where they effectively encode questions and corresponding tables from Wikipedia as seen in Table QA dataset. However, web tables in Wikipedia are notably flat in their layout, with the first row as the sole column header. The layout lends to a relational view of tables where each row is a tuple. Whereas, tables in domain-specific business or scientific documents often have a much more complex layout, including hierarchical row and column headers, in addition to having specialized vocabulary terms from that domain. To address this problem, we introduce the domain-specific Table QA dataset AITQA (Airline Industry Table QA). The dataset consists of 515 questions authored by human annotators on 116 tables extracted from public U.S. SEC filings (SEC Filings publicly available at: https://www.sec.gov/edgar.shtml) of major airline companies for the fiscal years 2017-2019. We also provide annotations pertaining to the nature of questions, marking those that require hierarchical headers, domain-specific terminology, and paraphrased forms. Our zero-shot baseline evaluation of three transformer-based SOTA Table QA methods - TaPAS (end-to-end), TaBERT (semantic parsing-based), and RCI (row-column encoding-based) - clearly exposes the limitation of these methods in this practical setting, with the best accuracy at just 51.8% (RCI). We also present pragmatic table pre-processing steps used to pivot and project these complex tables into a layout suitable for the SOTA Table QA models.


## Dataset

This repository contains the resources including data and code corresponding to the paper. Please refer to the paper if you are using them as below:

```
AIT-QA: Question Answering Dataset over Complex Tables in the Airline Industry, arxiv.org, 2021
```

The paper is also submitted to the [NeurIPS 2021 Datasets and Benchmarks Track](https://neurips.cc/Conferences/2021/CallForDatasetsBenchmarks) and can be found on openreview [here](https://openreview.net/forum?id=cB3OdLInAr9)   

First version of the data will be relased on 18 June, 2021.


<!-- A more detailed Usage or detailed explaination of the repository here -->
## Notes

* The current set maintainers are [MAINTAINERS.md](MAINTAINERS.md)
<!-- A Changelog allows you to track major changes and things that happen, https://github.com/github-changelog-generator/github-changelog-generator can help automate the process -->
Any changes or improvement to the dataset is logged in [CHANGELOG.md](CHANGELOG.md)

<!-- A notes section is useful for anything that isn't covered in the Usage or Scope. Like what we have below. -->

<!-- Questions can be useful but optional, this gives you a place to say, "This is how to contact this project maintainers or create PRs -->
If you have any questions please yse tge discussion feature and not issues. Create a new [issue here][issues] to flag dataset inconsistancies or improvements generally after a discussion.

We will allow Contributions to the repo as per [CONTRIBUTING.md](CONTRIBUTING.md)
