# dxitemspy

This package is a Python implementation of DXI, "DXI Mappings V2021P1 from Ellis, Randall P, Heather E Hsu, Jeffrey J Siracuse, Allan Walkey, Karen E Lasser, Brian C Jacobson, Corinne Andriola, Alexander Hoagland, Ying Liu, Chenlu Song, Tzu-Chun Kuo, and Arlene S Ash. “Development and Assessment of a New Framework for Disease Surveillance, Prediction and Risk Adjustment: The Diagnostic Items Classification System.” JAMA Health Forum. 2022; 3(3): e220276. doi:10.1001/jamahealthforum.2022.0276"

[![PyPI - Version](https://img.shields.io/pypi/v/dxitemspy.svg)](https://pypi.org/project/dxitemspy)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/dxitemspy.svg)](https://pypi.org/project/dxitemspy)

-----

**Table of Contents**

- [Installation](#installation)
- [Examples](#examples)
- [References](#references)
- [License](#license)


## Installation

```console
pip install dxitemspy
```

## Examples

Note that this package assumes that you have appropriately collected all valid ICD10-CM codes. 

When you have the codes, prepare those into a list structure. That's the only parameter needed.

```console
% python
>>> from pprint import pprint
>>> from dxitemspy.dxitems import DXIEngine
>>> de = DXIEngine()
>>> out = de.get_dxi(["E089", "I10"])
>>> pprint(out)
{'dx2dxi': {'E089': ['END',
                     'DXI1_END006',
                     'HIER_END001',
                     'HIER_END002',
                     'HIER_END003',
                     'HIER_END004',
                     'CCSR_END002',
                     'CCSR_END006'],
            'I10': ['CIR', 'DXI1_CIR002', 'HIER_CIR001', 'CCSR_CIR007']},
 'labels': ['CCSR_END006',
            'HIER_END004',
            'CCSR_CIR007',
            'CCSR_END002',
            'HIER_END003',
            'DXI1_END006',
            'CIR',
            'HIER_END002',
            'END',
            'HIER_CIR001',
            'HIER_END001',
            'DXI1_CIR002'],
 'labels_info': {'CCSR_CIR007': {'ch_abbrev': 'CCSR',
                                 'has_default_coeff': True,
                                 'label': 'Essential hypertension',
                                 'level': 1,
                                 'score': 298.36,
                                 'system': 'CCSR'},
                 'CCSR_END002': {'ch_abbrev': 'CCSR',
                                 'has_default_coeff': True,
                                 'label': 'Diabetes mellitus without '
                                          'complication',
                                 'level': 1,
                                 'score': 1992.61,
                                 'system': 'CCSR'},
                 'CCSR_END006': {'ch_abbrev': 'CCSR',
                                 'has_default_coeff': True,
                                 'label': 'Diabetes mellitus, due to '
                                          'underlying condition, drug or '
                                          'chemical induced, or other '
                                          'specified type',
                                 'level': 1,
                                 'score': -2351.11,
                                 'system': 'CCSR'},
                 'DXI1_CIR002': {'ch_abbrev': 'CIR',
                                 'label': 'Essential_hypertension',
                                 'level': 1,
                                 'system': 'DXI'},
                 'DXI1_END006': {'ch_abbrev': 'END',
                                 'has_default_coeff': True,
                                 'label': 'Diabetes_mellitus_secondary',
                                 'level': 1,
                                 'score': 4274.95,
                                 'system': 'DXI'},
                 'HIER_CIR001': {'ch_abbrev': 'CIR',
                                 'label': 'CIR_Hyperten',
                                 'level': 0},
                 'HIER_END001': {'ch_abbrev': 'END',
                                 'label': 'END_DM_Type_1',
                                 'level': 0},
                 'HIER_END002': {'ch_abbrev': 'END',
                                 'label': 'END_DM_Type_2',
                                 'level': 0},
                 'HIER_END003': {'ch_abbrev': 'END',
                                 'label': 'END_DM_Drug_Chem',
                                 'level': 0},
                 'HIER_END004': {'ch_abbrev': 'END',
                                 'label': 'END_DM_Other',
                                 'level': 0}},
 'score': 4274.95}
```

You can use the `labels` to construct a new feature matrix for other risk models.

The `score` uses the default coefficients used in the original paper. The score should be indicative of a concurrent estimation of annual spend.

## References

- [JAMA Paper](https://jamanetwork.com/journals/jama-health-forum/fullarticle/2790542)
- [Mapping Files](https://drive.google.com/drive/folders/1xpDGARdHVECtQkwEZpYRkTSD7rBbaUPg)
- [SAS Scripts](https://drive.google.com/drive/folders/1dNQqVotsoax7I1hEgYhXoweeV_cXjBEw)


## License

Please note that the original code sets are published under Creative Commons. 

`dxitemspy` is distributed under the terms of the [MIT](https://spdx.org/licenses/MIT.html) license, but its contents are subject to CC as well.
