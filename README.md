# A Short Guide to Oncomine Automation
## Objective
Replace slow and manual processes with automated workflows
## Software required:
## 1. [python3](https://www.python.org/download/releases/3.0/)
#### What does it do?
Python is a high-level, interpreted, general-purpose programming language. It is used to execute automate tasks and conduct data analysis.
## 2. [watchdog](https://pypi.org/project/watchdog/)
### What does it do?
Python API library and shell utilities to monitor file system events.
## 3.  [ion_automation](https://github.com/khzhu/ion_automation)
### What does it do?
The automated workflow to generate quality control plots/reports and select variants from Oncomine Focus and Myeloid Assay NGS sequencing data.

## Directory Structure

- oncomine solid
```
|— amplicon.dropout.dropoff 
|— downloads
|- dropoff
|- reports
```

- myeloidseq
```
|— amplicon.dropout.dropoff 
|— downloads
|- worksheet.dropoffs
|- reports
```

## Simplified step by step guide

1. get a copy of the myeloseq worksheet for the run from the **MOLECULAR LAB ONLY/NYU-MyeloSeqer/Worksheets-Wetlab** folder
2. drop the worksheet to the **worksheet.dropoffs** subfolder under the IonTorrent folder on the Molecular shared drive
3. kickstart the workflow to generate QC plots/reports, to filter and select confident calls, and to save variants in a csv and xlsx formats
4. copy CSV and dropout reports to the **MOLECULAR LAB ONLY/NYU-MyeloSeqer/Patient data**
