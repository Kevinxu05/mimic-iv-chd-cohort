# MIMIC-IV CHD cohort with radiology reports

Identify a patient-level congenital cardiovascular-malformation cohort in **MIMIC-IV v3.1** using ICD-9 **745–747** or ICD-10 **Q20–Q28**, then extract demographics, hospital diagnoses, procedures, admissions, radiology reports and discharge summaries into separate local CSVs.

The local run identified **4,528 unique patients**. These broad code ranges include congenital vascular malformations; the cohort is code-defined and has not been clinically adjudicated.

## Run

Python 3.10+ with no third-party packages. From the repository directory:

```powershell
py -3 .\build_chd_cohort.py --data-root "D:\Hang\SVP_project\MIMIC_data" --output-dir ".\results\CHD"
```

Replace the data path with your authorized local dataset directory. Use a new output directory for a fresh run. See [CHD_METHOD.md](CHD_METHOD.md) for selection rules, source layout, all generated files, validation, limitations and resume behavior. [build_chd_cohort.py](build_chd_cohort.py) contains the complete extraction code.

## Data and record scope

Patients qualify with at least one matching diagnosis in any diagnosis position and must exist in the EHR patients table. The exports contain all available records for those subjects, including admissions without qualifying CHD codes. The script also saves qualifying admission IDs for analyses requiring that narrower scope.

MIMIC-IV-Note v2.2 contains radiology reports and discharge summaries but no standalone consultation notes. The consultation CSV is a header-only placeholder for unavailable source data.

This repository distributes **code and documentation only**. Obtain authorized access to [MIMIC-IV v3.1](https://physionet.org/content/mimiciv/3.1/) and [MIMIC-IV-Note v2.2](https://physionet.org/content/mimic-iv-note/2.2/) through PhysioNet. Generated patient IDs, report text and clinical CSVs must remain within your authorized environment.

## Related project

[mimic-radiology-ehr-linkage](https://github.com/Kevinxu05/mimic-radiology-ehr-linkage) provides the separate general-purpose radiology–EHR linkage pipeline.
