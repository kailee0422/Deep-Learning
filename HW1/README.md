# DL Lab 1: Dataset and DataLoader

## Lab Objective
In this assignment, you should use PyTorch, `Dataset` and `DataLoader` in `torch.nn` to filter the root of files we assigned.

## Dataset Introduction
`CSI_data.json` contains three classes: `train`, `val`, and `test`. Each class has multiple roots of different files, which formats are:

`CLASS_NAME/npy/THE_GENDER_AND_COUNT/POSITION/TIME/FILE_NAME`

You need to filter out what we ask you.

**Example:**  
Give me the roots that contain `TIME` of `240509`.  
Part of the answer is shown below.

![image](https://github.com/user-attachments/assets/c9210671-2466-4cca-9476-0155d150b777)

## Homework Requirements
1. `CLASS_NAME` contains `Env3`.
2. `THE_GENDER_AND_COUNT` contains 2 females with no limit on the number of males.
3. `THE_GENDER_AND_COUNT` contains 1 female without any male.
4. `TIME` contains from `5/6 18:13:07` to `5/7 23:24:34` (same as `240506_181307` to `240507_232434`).
5. `CLASS_NAME` contains `Env3`, `THE_GENDER_AND_COUNT` contains just 1 male, `POSITION` contains `5_posi`, and `TIME` from `5/8 09:00` to `5/8 11:00`.

Save the answer for each requirement into an individual JSON file, named as follows:

`A1_studentID_studentName_{requirement}.json`

Your submissions will include 5 JSON files, as shown below:

- `A1_studentID_studentName_1.json`
- `A1_studentID_studentName_2.json`
- `A1_studentID_studentName_3.json`
- `A1_studentID_studentName_4.json`
- `A1_studentID_studentName_5.json`

## Rules
1. You should implement the homework by yourself. This assignment should be done individually. Please do not plagiarize the assignment. If plagiarism is found, the students involved will receive a score of zero.
2. Only PyTorch is allowed in this lab.
3. If the assignment format and files do not adhere to the regulations, the assignment score will be multiplied by 0.9.
4. If the assignment is missing or incomplete for any item, the assignment score will be deducted proportionally to the incompleteness.
5. If you submit your assignment late, your score will be multiplied by 0.9 for each day of delay.

## Submission
1. Please submit your code and answer JSON file. The filename should be `A1_studentID_studentName.ipynb` and the JSON files mentioned before. Compress them into a ZIP file, and the filename should be `A1_studentID_studentName.zip`.
2. Implement a `Dataset` and `DataLoader`.
3. A Report in PDF format, with the filename `A1_studentID_studentName.pdf`. The report needs to explain how you designed the `Dataset` and `DataLoader`, and why the answers are correct. The report should be at most 2 pages.

## Description of Code
Your code must be submitted following the format provided by the TAs. Additional sections can be included as necessary.

## Assignment Evaluation
- Code & model performances (40%)
- Report (60%)

## Tips
Clearly check the "Root name of the file."
