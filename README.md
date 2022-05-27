# User Guide to Oncomine Automation
## Workflow from run initiation to review of annotated variants
* Annotate variants from the oncomine annotator
* Focus on variants of interest
* Visualize and interpret variants
* Link variants to relevant clinical evidence

## Software required:
## 1. [python3](https://www.python.org/download/releases/3.0/)
Python is a high-level, interpreted, general-purpose programming language. It is used to execute automated tasks and conduct data analysis.
## 2. [watchdog](https://pypi.org/project/watchdog/)
Python API library and shell utilities to monitor file system events.
## 3.  [ion_automation](https://github.com/khzhu/ion_automation)
An in-house automated workflow to generate quality control plots/reports and select variants from Oncomine Focus and Myeloid Assay NGS sequencing data.

## Workflow Diagram
![This is a flowchart](https://github.com/khzhu/ion_automation/blob/main/docs/oncomine-workflow.png)

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

## Step by step guide to generate MyeloSeq automated report

1. create a new folder in the **/Molecular/IonTorrent/myeloseqer_test/amplicon.dropout.dropoff** folder for the run.
2. copy basecall QC matrix files from **/MOLECULAR LAB ONLY/NYU-MyeloSeqer/Patient data** to **amplicon.dropout.dropoff**
3. get a copy of the myeloseq worksheet for the run from the **MOLECULAR LAB ONLY/NYU-MyeloSeqer/Worksheets-Wetlab** folder
4. drop the worksheet to the **worksheet.dropoffs** subfolder under the IonTorrent folder on the Molecular shared drive

**Note**: The workflow automatically starts in a few seconds. It takes up to 10~30 minutes to generate QC plots/reports, 
to select confident calls, and to save filtered variants in a csv and excel format

5. copy CSV and dropout reports to the **/MOLECULAR LAB ONLY/NYU-MyeloSeqer/Patient data**

## Step by step guide to generate Oncomine Solid automated report

1. copy basecall QC matrix files from **/MOLECULAR LAB ONLY/NYU-MyeloSeqer/Patient data** to **/Molecular/IonTorrent/oncosolid_autoreport/amplicon.dropout.dropoff**
2. get a copy of the myeloseq worksheet for the run from the **MOLECULAR LAB ONLY/Oncomine Patient Data/Worksheets-Wetlab** folder
3. drop the worksheet of the run to the **worksheet** subfolder under the IonTorrent folder on the Molecular shared drive

**Note**: The workflow automatically starts in a few seconds. It takes up to 10~20 minutes to generate QC plots/reports, 
to select confident calls, and to save filtered variants in a csv and excel format

4. copy CSV and dropout reports to the **/MOLECULAR LAB ONLY/Oncomine Patient Data/Patient data**

## Step by step guide to generate report manually

## 1. Oncomine Solid

1. log into the ionreporter server as an admin user via HPC
2. go to the **ion_report** directory
3. complete steps 1 ~ 3 in the auto report section
4. execute ion_runner.py
```
ssh ionadmin@ionreporter.nyumc.org
cd /home/ionadmin/ion_report
python3 ion_runner.py /mnt/Z_drive/Molecular/IonTorrent/oncosolid_autoreport/worksheet/22-MGON9.xlsm
```

## 2. MyeloSeq

1. log into the ionreporter server as an admin user via HPC
2. go to the **myeloseq_report** directory
3. complete steps 1 ~ 3 in the auto report section
4. execute myelo_runner.py
```
ssh ionadmin@ionreporter.nyumc.org
cd /home/ionadmin/myeloseq_report
python3 myelo_runner.py /mnt/Z_drive/Molecular/IonTorrent/myeloseqer_test/worksheet.dropoffs/22-MGMQ24.xlsm
```

## Maintaining automated workflow

## 1. ion_report workflow
1. log into the ionreporter server as an admin user via HPC
2. change to the ion_report directory
3. start or stop the ion_watchdog daemon process
```
ssh ionadmin@ionreporter.nyumc.org
cd /home/ionadmin/myeloseq_report
sh io_watchdog.sh start [stop]
```

## 2. myelo_report workflow
1. log into the ionreporter server as an admin user via HPC
2. change to the myeloseq_report directory
3. start or stop the myelo_watchdog daemon process
```
ssh ionadmin@ionreporter.nyumc.org
cd /home/ionadmin/myeloseq_report
sh myelo_watchdog.sh start [stop]
```
