# 🌐 ENHANCE: Total-Body PET/CT Dataset Standardization

ScanVerse360 aims to open source and standardize Total-Body PET/CT datasets. We
have utilized a proposed standardization methodology from MedUniWien as a
baseline approach and updated accordingly in our efforts to contribute to the
open-source initiative. It's designed to ensure easy navigation, consistent
representation, and programmable data retrieval.

## 📂 Directory Structure

```
sv360_metadata.json
CohortNameA_99990130_99990230/
├── ...
├── ...
│   ├── ...
CohortNameB_99990130_99990230/
├── metadata.json
├── sub001/
│   ├── scan01/
│   │   ├── PT/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── ACCT/
│   ├── scan02/
│   │   ├── PT/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── ACCT/
├── sub002/
│   ├── scan01/
│   │   ├── PT/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── ACCT/
│   ├── scan02/
│   │   ├── PT/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── ACCT/
```

## Root Directory Structure

Top level directory structure consists of cohort (or Project Folders); these
folders serve as groupings for studies. Folder naming should be unique and
follow the naming convention of: `PROJECTNAME_STARTDATE_ENDDATE`.

Both start date and end date should be in the format of: `YYYYMMDD`

## 🔍 `sv360_metadata.json` Structure

The `sv360_metadata.json` file serves as a comprehensive overview & description
of available projects within the collective open source data set:

```json
[
    {
        "PROJECT_NAME": "Project 1",
        "SHORT_DESC": "Lorem ipsum 1", 
        "START": "YYYYMMDD1",
        "END": "YYYYMMDD1",
        "OBJECTIVE": "Lorem Ipsum 1",
        "PRINCIPAL_INVESTIGATOR": "Name 1",
        "PRINCIPAL_INVESTIGATOR_CONTACT": "contact 1",
        "AVAIL_DATA": "Lorem Ipsum 1",
        "INSTITUTIONS": [
            {
                "NAME": "Institution 1",
                "CT_PARM": {
                    "MACHINE": "SIEMENS",
                    "SETTINGS": "120kV,80mAs",
                    "MODALITY": "CT",
                    "STUDY_TYPE": "STATIC (3D)"
                },
                "PT_PARM": {
                    "MACHINE": "SIEMEN",
                    "MODALITY": "PT",
                    "RADIOSOTOPE": "F-18 FDG",
                    "INJECTED_DOSE": "3.7-5.2 MBq/kg",
                    "SCAN DURATION": "60-90 MIN POST INJECTION"
                },
                "SUB_DEMOGRAPHIC": {
                    "AGE_RANGE": "45-75",
                    "GENDER_DISTRIBUTION": "55% MALE, 45% Female",
                    "TOTAL_SUB": "> 800"
                }
            },
            {
                "NAME": "Institution 2",
                "CT_PARM": {
                    "MACHINE": "SIEMENS",
                    "SETTINGS": "Custom settings for Institution 2",
                    "MODALITY": "CT",
                    "STUDY_TYPE": "Custom study type for Institution 2"
                },
                "PT_PARM": {
                    "MACHINE": "SIEMEN",
                    "MODALITY": "PT",
                    "RADIOSOTOPE": "Custom radiosotope for Institution 2",
                    "INJECTED_DOSE": "Custom dose for Institution 2",
                    "SCAN DURATION": "Custom duration for Institution 2"
                },
                "SUB_DEMOGRAPHIC": {
                    "AGE_RANGE": "Custom age range for Institution 2",
                    "GENDER_DISTRIBUTION": "Custom gender distribution for Institution 2",
                    "TOTAL_SUB": "Custom total subjects for Institution 2"
                }
            }
        ]
    },
    {
        "PROJECT_NAME": "Project 2",
        "SHORT_DESC": "Lorem ipsum 2", 
        "START": "YYYYMMDD2",
        "END": "YYYYMMDD2",
        "OBJECTIVE": "Lorem Ipsum 2",
        "PRINCIPAL_INVESTIGATOR": "Name 2",
        "PRINCIPAL_INVESTIGATOR_CONTACT": "contact 2",
        "AVAIL_DATA": "Lorem Ipsum 2",
        "INSTITUTIONS": [
            {
                "NAME": "Institution 3",
                "CT_PARM": {
                    "MACHINE": "SIEMENS",
                    "SETTINGS": "Settings for Institution 3",
                    "MODALITY": "CT",
                    "STUDY_TYPE": "Study type for Institution 3"
                },
                "PT_PARM": {
                    "MACHINE": "SIEMEN",
                    "MODALITY": "PT",
                    "RADIOSOTOPE": "Radiosotope for Institution 3",
                    "INJECTED_DOSE": "Dose for Institution 3",
                    "SCAN DURATION": "Duration for Institution 3"
                },
                "SUB_DEMOGRAPHIC": {
                    "AGE_RANGE": "Age range for Institution 3",
                    "GENDER_DISTRIBUTION": "Gender distribution for Institution 3",
                    "TOTAL_SUB": "Total subjects for Institution 3"
                }
            }
        ]
    }
]


```

## 🗝 Key for Directories

- **PT**: Positron Emission Tomography
- **ACCT**: Computed Tomography - Attenuation Correction
- **static**: Static PET data
- **dynamic**: Dynamic PET data
- **listmode**: List-mode PET data
- **parametric**: Parametric PET images

## 🔍 `metadata.json` Structure

The `metadata.json` file serves as a comprehensive overview of the dataset for
each cohort/project:

```json
{
    "cohort": "LungCancerPatients",
    "description": "A collection of PET/CT datasets for lung cancer patients.",
    "directory_key": {
        "PET": "Positron Emission Tomography",
        "ACCT": "Computed Tomography - Attenuation Correction",
        "static": "Static PET data",
        "dynamic": "Dynamic PET data",
        "listmode": "List-mode PET data",
        "parametric": "Parametric PET images"
    },
    "expected_datasets": ["static", "dynamic", "listmode", "parametric", "ACCT"],
    "subjects": [
        {
            "id": "sub001",
            "scans": [
                {
                    "scan_id": "scan01",
                    "datasets": {
                        "static": true,
                        "dynamic": true,
                        "listmode": true,
                        "parametric": true,
                        "ACCT": true
                    }
                },
                {
                    "scan_id": "scan02",
                    "datasets": {
                        "static": true,
                        "dynamic": true,
                        "listmode": true,
                        "parametric": true,
                        "ACCT": true
                    }
                }
            ]
        },
        {
            "id": "sub002",
            "scans": [
                {
                    "scan_id": "scan01",
                    "datasets": {
                        "static": true,
                        "dynamic": true,
                        "listmode": true,
                        "parametric": true,
                        "ACCT": true
                    }
                },
                {
                    "scan_id": "scan02",
                    "datasets": {
                        "static": true,
                        "dynamic": false,
                        "listmode": false,
                        "parametric": true,
                        "ACCT": true
                    }
                }
            ]
        }
    ]
}
```

## 📌 Generating `metadata.json` from Folder Structure

Before diving into generating `metadata.json`, there are naming conventions to
be followed for subjects and their scans:

- **Subjects**: Each subject should have a name in the format `subXXXX` where
  `XXXX` is a unique identifier for the subject. For example: `sub0012`,
  `sub1204`.
  
- **Scans**: Each longitudinal scan for a subject should be named as `scanXXX`
  where `XXX` is the identifier for that scan. For example: `scan001`,
  `scan032`.

Adhering to these conventions ensures accurate and consistent metadata
generation. We provide a convenient Python script to generate `metadata.json`
directly from your dataset's root folder. It works as long as the folder
conventions we've described are adhered to.

### 🔧 Prerequisites

Make sure you have Python installed on your machine.

### 🚀 How to use

1. Copy the script below:

```python
import os
import json

def generate_metadata(root_folder):
    metadata = {
        "cohort": os.path.basename(root_folder),
        "description": f"A collection of PET/CT datasets for {os.path.basename(root_folder)}.",
        "directory_key": {
            "PT": "Positron Emission Tomography",
            "ACCT": "Computed Tomography - Attenuation Correction",
            "static": "Static PET data",
            "dynamic": "Dynamic PET data",
            "listmode": "List-mode PET data",
            "parametric": "Parametric PET images"
        },
        "expected_datasets": ["static", "dynamic", "listmode", "parametric", "ACCT"],
        "subjects": []
    }

    for subject in sorted(os.listdir(root_folder)):
        subject_path = os.path.join(root_folder, subject)
        if os.path.isdir(subject_path) and "sub" in subject:
            subject_data = {
                "id": subject,
                "scans": []
            }
            for scan in sorted(os.listdir(subject_path)):
                scan_path = os.path.join(subject_path, scan)
                if os.path.isdir(scan_path) and "scan" in scan:
                    scan_data = {
                        "scan_id": scan,
                        "datasets": {
                            "static": os.path.exists(os.path.join(scan_path, "PET", "static")),
                            "dynamic": os.path.exists(os.path.join(scan_path, "PET", "dynamic")),
                            "listmode": os.path.exists(os.path.join(scan_path, "PET", "listmode")),
                            "parametric": os.path.exists(os.path.join(scan_path, "PET", "parametric")),
                            "ACCT": os.path.exists(os.path.join(scan_path, "ACCT"))
                        }
                    }
                    subject_data["scans"].append(scan_data)
            metadata["subjects"].append(subject_data)

    with open(os.path.join(root_folder, 'metadata.json'), 'w') as f:
        json.dump(metadata, f, indent=4)

    print(f"metadata.json generated in {root_folder}")

# To execute the script, just call the generate_metadata function with your root folder path.
# For example: generate_metadata('/path/to/your/CohortName')
```

2. Save the script in a `.py` file, e.g., `generate_metadata.py`.
3. Run the script and provide the root folder path. 

Example:

```bash
python generate_metadata.py
```

4. After execution, `metadata.json` will be generated in the provided root folder.
