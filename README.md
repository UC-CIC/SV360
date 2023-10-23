# 🌐 ENHANCE: Total-Body PET/CT Dataset Standardization

ScanVerse360 aims to open source and standardize Total-Body PET/CT datasets. We
have utilized a proposed standardization methodology from MedUniWien as a
baseline approach and updated accordingly in our efforts to contribute to the
open-source initiative. It's designed to ensure easy navigation, consistent
representation, and programmable data retrieval.

## 📂 Directory Structure

```
sv360_metadata.json
cohort_name_a__99990130__99990230/
├── ...
├── ...
│   ├── ...
cohort_name_b__99990130__99990230/
├── metadata.json
├── sub001/
│   ├── scan01/
│   │   ├── pt/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── acct/
│   ├── scan02/
│   │   ├── pt/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── acct/
├── sub002/
│   ├── scan01/
│   │   ├── pt/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── acct/
│   ├── scan02/
│   │   ├── pt/
│   │   │   ├── static/
│   │   │   ├── dynamic/
│   │   │   ├── listmode/
│   │   │   ├── parametric/
│   │   ├── acct/
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
        "project_name": "Project 1",
        "short_desc": "Lorem ipsum 1", 
        "start": "YYYYMMDD1",
        "end": "YYYYMMDD1",
        "objective": "Lorem Ipsum 1",
        "principal_investigator": "Name 1",
        "principal_investigator_contact": "contact 1",
        "avail_data": "Lorem Ipsum 1",
        "institutions": [
            {
                "name": "Institution 1",
                "ct_parm": {
                    "machine": "SIEMENS",
                    "settings": "120kV,80mAs",
                    "modality": "CT",
                    "study_type": "STATIC (3D)"
                },
                "pt_parm": {
                    "machine": "SIEMEN",
                    "modality": "PT",
                    "radiosotope": "F-18 FDG",
                    "injected_dose": "3.7-5.2 MBq/kg",
                    "scan_duration": "60-90 MIN POST INJECTION"
                },
                "sub_demographic": {
                    "age_range": "45-75",
                    "gender_distribution": "55% MALE, 45% Female",
                    "total_sub": "> 800"
                }
            },
            {
                "name": "Institution 2",
                "ct_parm": {
                    "machine": "SIEMENS",
                    "settings": "Custom settings for Institution 2",
                    "modality": "CT",
                    "study_type": "Custom study type for Institution 2"
                },
                "pt_parm": {
                    "machine": "SIEMEN",
                    "modality": "PT",
                    "radiosotope": "Custom radiosotope for Institution 2",
                    "injected_dose": "Custom dose for Institution 2",
                    "scan_duration": "Custom duration for Institution 2"
                },
                "sub_demographic": {
                    "age_range": "Custom age range for Institution 2",
                    "gender_distribution": "Custom gender distribution for Institution 2",
                    "total_sub": "Custom total subjects for Institution 2"
                }
            }
        ]
    },
    {
        "project_name": "Project 2",
        "short_desc": "Lorem ipsum 2", 
        "start": "YYYYMMDD2",
        "end": "YYYYMMDD2",
        "objective": "Lorem Ipsum 2",
        "principal_investigator": "Name 2",
        "principal_investigator_contact": "contact 2",
        "avail_data": "Lorem Ipsum 2",
        "institutions": [
            {
                "name": "Institution 3",
                "ct_parm": {
                    "machine": "SIEMENS",
                    "settings": "Settings for Institution 3",
                    "modality": "CT",
                    "study_type": "Study type for Institution 3"
                },
                "pt_parm": {
                    "machine": "SIEMEN",
                    "modality": "PT",
                    "radiosotope": "Radiosotope for Institution 3",
                    "injected_dose": "Dose for Institution 3",
                    "scan_duration": "Duration for Institution 3"
                },
                "sub_demographic": {
                    "age_range": "Age range for Institution 3",
                    "gender_distribution": "Gender distribution for Institution 3",
                    "total_sub": "Total subjects for Institution 3"
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
        "pet": "Positron Emission Tomography",
        "acct": "Computed Tomography - Attenuation Correction",
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
                        "acct": true
                    }
                },
                {
                    "scan_id": "scan02",
                    "datasets": {
                        "static": true,
                        "dynamic": false,
                        "listmode": false,
                        "parametric": true,
                        "acct": true
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
            "pt": "Positron Emission Tomography",
            "acct": "Computed Tomography - Attenuation Correction",
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
                            "acct": os.path.exists(os.path.join(scan_path, "ACCT"))
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
