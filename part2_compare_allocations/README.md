# EduAll, part 2: comparing two allocations

Your group allocated CHF 500,000 among 500 applicants. So did another group, whose method you will infer. This notebook
evaluates both allocations with the same code and the same standards, and gives you the evidence for your comparison
report and your final presentation.

## Run the comparison for your group

| Notebook | Colab |
|---|---|
| Comparison of your allocation and the one you received | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/part2_compare_allocations/EduAll_2_compare_allocations.ipynb) |

1. Click the **Open in Colab** badge, then choose *File → Save a copy in Drive*. Work in your copy: the executed
   notebook then stays in your Drive for the hand-in.
2. Add your Gemini key for Part 9: click the 🔑 icon in the left bar → *Add new secret* → name `GEMINI_API_KEY` →
   switch on *Notebook access*.
3. Choose *Runtime → Run all* and accept the access to your Drive. The first cells create the folder
   `MyDrive/EduAll_part2`, download the four data files into it, and show two upload buttons: first your group's
   allocation file, then the file you received. Each file has two columns: student ID and amount in CHF.
4. After two to three minutes, the results sit in `MyDrive/EduAll_part2/comparison_our_allocation_vs_received_allocation/`:
   `summary.txt`, `comparison_report.html`, and the folders `tables` and `figures`.

A second run finds everything in the folder and goes straight to the analyses.

## Follow the lecture: the example run

| Notebook | Colab |
|---|---|
| Example run on two simulated allocations, Navy and Sky | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/part2_compare_allocations/example/EduAll_2_compare_allocations_example_run.ipynb) |

The example notebook opens with every result already computed. The same results come as one web page,
[`example/comparison_report_example.html`](example/comparison_report_example.html): download it and open it in any
browser. The answers in Part 9 of the example come from stored answers written by Claude (Anthropic) from the same
prompts; each answer names its source. Your own run calls Gemini with your key.

## What your group hands in

- the comparison report;
- the results of the notebook: the executed notebook (your Drive copy) and its results folder;
- the final presentation.

## What this folder contains

```
EduAll_2_compare_allocations.ipynb        the comparison notebook for your group
data/
  EduAll_features.csv                     the CSV you know (44 columns) plus 34 columns read from the 500 forms
  EduAll_feature_dictionary.csv           one line per new column, with its meaning
  EduAll_evidence.json                    the sentences from the forms behind each new column
  EduAll_forms.json                       the full text of the 500 forms, which Gemini reads in Part 9
example/
  EduAll_2_compare_allocations_example_run.ipynb   the notebook run on the Navy and Sky allocations
  comparison_report_example.html          the same results as one web page
  own_allocation_example.csv              Navy, the example "own" allocation
  other_allocation_example.csv            Sky, the example "other" allocation
  llm_cache.json                          the stored example answers of Part 9
```

The notebook downloads the files of `data/` by itself, so a copy of this folder on your computer is optional.
