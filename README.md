# Hidden Markov Model for Hard Disk Drive Failure Detection

Hard Disk Drives (HDDs) are critical components in computer systems, serving as primary non-volatile storage. Detecting potential failures in HDDs is crucial for maintaining the efficiency of various devices, including servers and laptops. This project implements a Hidden Markov Model (HMM) for the detection of HDD failures using the Backblaze dataset, which contains daily snapshots of SMART data for each operational hard drive.

## Implementation
![Model_Pipeline](https://github.com/ronithrnair/HMM-for-HDD-Failure/assets/100126824/e0dae762-87f1-4b36-8d2e-d103731f78f4)

### Preprocessing

The dataset initially contained 80 SMART attribute columns. After normalization and removal of redundant or missing data, 21 SMART attribute columns were retained for further analysis.

### Clustering

To transform continuous attribute values into discrete ranges, K-Means clustering was employed. The dataset was then split into two groups: failed disks and working disks. Equal numbers of disks were chosen from each group, and a 3:1 train-test split was performed within each group.

### Modelling

HMMs were created for working and failed disks separately, with individual HMMs corresponding to each SMART disk attribute. The number of hidden states for each HMM was set to 5. Training was conducted using the Baum-Welch algorithm on multiple sequences of data for 3 iterations to find the most optimal set of hidden sequences.

## Results

- Training Dataset: 1116 working and failed hard disk drives.
- Testing Dataset: 744 disks, with an equal number of working and failed disks.

The model demonstrated strong performance on the testing set, achieving an accuracy of 92%. Specific metrics include:

- False Alarm Rate (FAR): 11%
- Fault Detection Rate (FDR): 96%

## Setup

1. Use `poetry` to install dependencies:

```bash
poetry install
```

2. Download the [dataset](https://drive.google.com/file/d/1OqAJBbpfvXlikiQRVF6S6FSlYRFRFV-q/view?usp=sharing).

3. Extract the dataset and place the files into the `HMM-for-HDD-Failure/input` directory.

## Run

Execute the following command to run the Jupyter notebook:

```bash
poetry run jupyter notebook
```

This will open a Jupyter notebook where you can explore and run the provided code.

Feel free to reach out if you have any questions or need further assistance!
