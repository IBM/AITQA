<!-- This should be the location of the title of the repository, normally the short name -->
# AIT-QA: Question Answering Dataset over Complex Tables in the Airline Industry 

<!-- Build Status, is a great thing to have at the top of your repository, it shows that you take your CI/CD as first class citizens -->
<!-- [![Build Status](https://travis-ci.org/jjasghar/ibm-cloud-cli.svg?branch=master)](https://travis-ci.org/jjasghar/ibm-cloud-cli) -->

<!-- Not always needed, but a scope helps the user understand in a short sentance like below, why this repo exists -->
## Abstract

###### Recent advances in transformers have enabled Table Question Answering (Table QA) systems to achieve high accuracy and SOTA results on open domain datasets like WikiTableQuestions and WikiSQL. Such transformers are frequently pre-trained on open-domain content such as Wikipedia, where they effectively encode questions and corresponding tables from Wikipedia as seen in Table QA dataset. However, web tables in Wikipedia are notably flat in their layout, with the first row as the sole column header. The layout lends to a relational view of tables where each row is a tuple. Whereas, tables in domain-specific business or scientific documents often have a much more complex layout, including hierarchical row and column headers, in addition to having specialized vocabulary terms from that domain. To address this problem, we introduce the domain-specific Table QA dataset AITQA (Airline Industry Table QA). The dataset consists of 515 questions authored by human annotators on 116 tables extracted from public U.S. SEC filings (SEC Filings publicly available at: https://www.sec.gov/edgar.shtml) of major airline companies for the fiscal years 2017-2019. We also provide annotations pertaining to the nature of questions, marking those that require hierarchical headers, domain-specific terminology, and paraphrased forms. Our zero-shot baseline evaluation of three transformer-based SOTA Table QA methods - TaPAS (end-to-end), TaBERT (semantic parsing-based), and RCI (row-column encoding-based) - clearly exposes the limitation of these methods in this practical setting, with the best accuracy at just 51.8% (RCI). We also present pragmatic table pre-processing steps used to pivot and project these complex tables into a layout suitable for the SOTA Table QA models.


## Dataset

This repository contains the resources including data and code corresponding to the paper. Please consider refering to the paper draft if you are using them, as below:

```
@misc{
aitqaNeurips2021draft,
title={AIT-QA: Question Answering Dataset over Complex Tables in the Airline Industry},
author={Yannis Katsis and Saneem Chemmengath and Vishwajeet Kumar and Samarth Bharadwaj and Mustafa Canim and Michael Glass and Alfio Gliozzo and Feifei Pan and Jaydeep Sen and Karthik Sankaranarayanan and Soumen Chakrabarti},
booktitle={under submission at NeurIPS 2021 Datasets and Benchmarks Track Round 1},
year={2021},
url={https://openreview.net/forum?id=cB3OdLInAr9}
}

@misc{katsis2021aitqa,
      title={AIT-QA: Question Answering Dataset over Complex Tables in the Airline Industry}, 
      author={Yannis Katsis and Saneem Chemmengath and Vishwajeet Kumar and Samarth Bharadwaj and Mustafa Canim and Michael Glass and Alfio Gliozzo and Feifei Pan and Jaydeep Sen and Karthik Sankaranarayanan and Soumen Chakrabarti},
      year={2021},
      eprint={2106.12944},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```



The paper is also submitted to the [NeurIPS 2021 Datasets and Benchmarks Track](https://neurips.cc/Conferences/2021/CallForDatasetsBenchmarks) and can be found on openreview [here](https://openreview.net/forum?id=cB3OdLInAr9)   

Arxiv link: https://arxiv.org/abs/2106.12944


## Content and format
Inside the `raw_data` folder you will find `dev_questions.jsonl` and `dev_tables.jsonl`. Both files can be read line by line, where each line is a serialized JSON object. The test questions and tables will be released upon acceptance of the dataset paper in submission (details above).

### Question, answers, table_id, and other annotations
The instances in `dev_questions.jsonl` looks like the follwing:
```json
{
  "id": "dev-0",
  "table_id": "tab-0",
  "question": "How much money did United spend for aircraft fuel in 2016?",
  "answers": ["$5,813"],
  "type": "KPI-driven",
  "row_hierarchy_needed": "No",
  "paraphrase_group": "para-5"
}
```
The fields represent the follwing:
- `id`: The ID of this data instance.
- `table_id`: The ID of the table to which questions is addressed.
- `question`: The question string.
- `answers`: A list containing answer(s) to the question.
- `type`: The type of information the question is about. It is either `KPI-driven` (questions that inquiry about Key Performance Indicators (KPIs) in airline industry) or `Table-driven` (questions on other concepts).
- `row_hierarchy_needed`: If finding the answer relies on the row header hierarchy.
- `paraphrase_group`: The ID of paraphrase group. A praphrase group is set of instances with questions which are paraphrases of each other.  `''` when the question does not have any paraphrase.

### Tables
The instances in `dev_tables.jsonl` looks like the follwing:
```json
{  
  "id": "tab-5",
  "column_header": [
    ["At December 31,", "2018"],
    ["At December 31,", "2017 (a)"]
  ],
  "row_header": [
    ["Current assets:", "Cash and cash equivalents"],
    ["Current assets:", "Short-term investments"],
    ["Current assets:", "Receivables, less allowance for doubtful accounts 2018—$8; 2017—$7)"],
    ["Current assets:", "Aircraft fuel, spare parts and supplies, less obsolescence allowance (2018—$412; 2017—$354)"],
    ["Current assets:", "Prepaid expenses and other"],
    ["Current assets:", "Total current assets"],
    ["Owned-", "Operating property and equipment:", "Flight equipment"],
    ["Owned-", "Operating property and equipment:", "Other property and equipment"],
    ["Owned-", "Operating property and equipment:", "Total owned property and equipment"],
    ["Owned-", "Operating property and equipment:", "Less-Accumulated depreciation and amortization"],
    ["Owned-", "Operating property and equipment:", "Total owned property and equipment, net"],
    ["Owned-", "Operating property and equipment:", "Purchase deposits for flight equipment"],
    ["Capital leases-", "Flight equipment"],
    ["Capital leases-", "Other property and equipment"],
    ["Capital leases-", "Total capital leases"],
    ["Capital leases-", "Less-Accumulated amortization"],
    ["Capital leases-", "Total capital leases, net"],
    ["Capital leases-", "Total operating property and equipment, net"],
    ["Other assets:", "Goodwill"],
    ["Other assets:", "Intangibles, less accumulated amortization (2018-$1,380; 2017-$1,313)"],
    ["Other assets:", "Restricted cash"],
    ["Other assets:", "Notes receivable, net"],
    ["Other assets:", "Investments in affiliates and other, net"],
    ["Other assets:", "Total other assets"],
    ["Total assets"]
  ],
  "data": [
    ["$1,694", "$1,482"],
    ["2,256", "2,316"],
    ["1,346", "1,340"],
    ["985", "924"],
    ["913", "1,071"],
    ["7,194", "7,133"],
    ["31,607", "28,692"],
    ["7,919", "6,946"],
    ["39,526", "35,638"],
    ["(12,760)", "(11,159)"],
    ["26,766", "24,479"],
    ["1,177", "1,344"],
    ["1,029", "1,151"],
    ["11", "11"],
    ["1,040", "1,162"],
    ["(654)", "(777)"],
    ["386", "385"],
    ["28,329", "26,208"],
    ["4,523", "4,523"],
    ["3,159", "3,539"],
    ["105", "91"],
    ["516", "46"],
    ["966", "806"],
    ["9,269", "9,005"],
    ["$44,792", "$42,346"]
  ]
}
```
The fields represent the following:
- `id`: The Table ID.
- `column_header`: A list of column names in the table. Column names can be hierarchical and sublist captures the order of hierarchy.
- `row_header`: A list of row headers in the tbale. Row headers can be hierarchical and sublist captures the order of hierarchy. 
- `data`: A list of rows. Each row is a list of row entries.

<!-- A more detailed Usage or detailed explaination of the repository here -->
## Notes

* The current set maintainers are [MAINTAINERS.md](MAINTAINERS.md)
<!-- A Changelog allows you to track major changes and things that happen, https://github.com/github-changelog-generator/github-changelog-generator can help automate the process -->
Any changes or improvement to the dataset is logged in [CHANGELOG.md](CHANGELOG.md)

<!-- A notes section is useful for anything that isn't covered in the Usage or Scope. Like what we have below. -->

<!-- Questions can be useful but optional, this gives you a place to say, "This is how to contact this project maintainers or create PRs -->
If you have any questions please yse tge discussion feature and not issues. Create a new [issue here][issues] to flag dataset inconsistancies or improvements generally after a discussion.

We will allow Contributions to the repo as per [CONTRIBUTING.md](CONTRIBUTING.md)
