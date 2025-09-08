# Experiment Report

## Introduction

In this report, we describe the design and implementation of a custom
`CSI_data` class and its integration with PyTorch's `DataLoader`. The
focus is on filtering data based on root name of file, various
requirements, and exporting the results to JSON files for different
dataset splits (**train, val, test**).

## Materials and Methods

This experiment utilizes the `CSI_data` dataset, which is divided into
train, val, and test splits. The objective is to output results based on
five different requirements. To achieve this, several key functions were
designed to process and filter the data.

-   The data is loaded through the
    `__init__(self, split='train', requirement=1)` function.
    -   **split** specifies the dataset split (train, val, test).\
    -   **requirement** defines the filtering criteria (five
        requirements).
-   The preprocessing is done via
    `filter_data(self, data_split, requirement)` which filters and
    formats the data.

The CSI_data.json file is split into **train, val, test**, each
containing file paths:

    CLASS_NAME/npy/THE_GENDER_AND_COUNT/POSITION/TIME/random_characters

### Dataset Components

-   **CLASS_NAME**: `Env0` to `Env5` for train, `val_set` and `test_set`
    for val/test.\
-   **THE_GENDER_AND_COUNT / POSITION**: Counts per class, visible in
    output.\
-   **TIME**: Format `YYMMDD_HHMMSS`.

### Requirements

1.  **Requirement 1**: Check if `CLASS_NAME` contains `Env3`.\
2.  **Requirement 2**: Identify entries containing **two females** in
    `THE_GENDER_AND_COUNT`. Used counting instead of regex due to cases
    like `F2M1M3F3`.\
3.  **Requirement 3**: Regex
    `re.match(r'Female?', THE_GENDER_AND_COUNT)` to find classes with
    **one female and no males**.\
4.  **Requirement 4**: Time filter `(start_time <= TIME <= end_time)`
    for **5/6 18:13:07 → 5/7 23:24:34**.\
5.  **Requirement 5**: Combination of four conditions:
    -   `CLASS_NAME` contains `Env3`.\
    -   Regex `re.match(r'Male?', THE_GENDER_AND_COUNT)` → only one
        male.\
    -   `POSITION` contains `5_posi`.\
    -   `TIME` between **5/8 09:00 → 5/8 11:00**.

### Supporting Functions

-   `__len__(self)`: Returns dataset size.\
-   `__getitem__(self, index)`: Returns individual samples.

### Output

-   Results are saved as `A1_313834006_李崇楷_{req}.json`.\

-   Outputs number of matches per split & requirement.\

-   If no match:

        {split} set, Requirement {requirement}: No matching data found.

-   Saves with message:

        Saved combined output for Requirement {requirement} to ./A1_313834006_李崇楷_{requirement}.json

## Results

You can view its content from the above JSON file (in zip), with the
same format as the CSI_data dataset.

## Code
You can run on colab or local

<a target="_blank" href="https://colab.research.google.com/github/kailee0422/Deep-Learning/blob/main/HW1/DL_A1.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>
