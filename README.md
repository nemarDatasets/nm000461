[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.nm000461-blue)](https://doi.org/10.82901/nemar.nm000461)

# iEEG networks preprocessing study (Pennsieve 355): functional-connectivity networks, derivative BIDS-iEEG

This is a **derivative** dataset. It repackages the release "iEEG networks preprocessing study" by Haoer Shi, Akash Pattnaik and
Erin Conrad on Pennsieve Discover (dataset 355 version 1, doi:10.26275/4p8l-n5kt, Penn CNT), the data of
Shi H, Pattnaik AR, et al. "Utility of intracranial EEG networks depends on re-referencing and connectivity choice",
Brain Communications 2024;6(3):fcae165, doi:10.1093/braincomms/fcae165 (the article's data availability statement points to this DOI).
It contains **no time series**: the raw iEEG is on iEEG.org (recording names in participants.tsv, `ieeg_org_recording`).
Code: https://github.com/penn-cnt/CNT_Preprocessing_Toolkit (demo/ana_pipeline.m).

## Contents

- `participants.tsv`: 148 patients (127 HUP, 21 MUSC) with at least one network file; 125 in the grey/white (gw)
  set, 96 in the left/right (LR) set. Columns from the released `patientList.mat` files (iEEG.org recording name, sampling rate,
  ILAE, Engel, seizure-onset laterality/region, temporal flag). The Pennsieve release has no age or sex; for the 53 HUP patients
  that are also in OpenNeuro ds004100 (NEMAR on004100, CC0) age and sex are copied from that dataset's participants.tsv
  (`demographics_source`). patientList rows without network files: none.
- `sub-<label>/ieeg/sub-<label>_task-interictal_acq-<gw|LR>_run-<n>_connectivity.mat` + `.json` (1105 files; listed in
  `.bidsignore`, not a BIDS file type): one file per patient, channel set and 2-minute interictal epoch (run 1-5), byte-identical to
  `sourcedata/pennsieve-355-v1/files/<centre>/<set>/result/<patient>_<n>.mat`. Variable `results` = re-referencing (CAR, bipolar) x
  24 measures (Pearson, squared Pearson, cross-correlation; coherence, phase-locking value and relative entropy in delta 0.5-4,
  theta 4-8, alpha 8-12, beta 12-30, gamma 30-80, ripple 80-250 and broadband 0.5-250 Hz) x channel x channel (LR: x hemisphere, 36
  standard slots); `full_ind` = channel masks. The JSON sidecar gives these dimensions, the iEEG.org recording, and for the gw set
  the channel names from `patientList.chan_gw` when their number equals the network size (298 files; 327 files where
  it does not, noted in the sidecar).
- `sourcedata/pennsieve-355-v1/`: every released file (results, four `patientList.mat`, Pennsieve manifest/readme).
  `SOURCE_MANIFEST.json` lists the original SHA-256 of each file. Files are byte-identical to the release except the MAT-file header
  creation dates, which were set to day 01 (weekday and time removed, same length).

Related NEMAR datasets: on004100 (OpenNeuro ds004100, HUP iEEG, overlapping HUP patients); nm000438 (Penn epilepsy iEEG, PennEPI).

## Privacy

All files were scanned (text, MAT strings and headers) for names, initials, record numbers, full dates and ages above 89. Patient
codes (HUP###, MP####) and iEEG.org recording names are the pseudonyms used in the public releases. No dates are present apart from
file-creation timestamps (scrubbed as above). Key status: destroyed (we hold no mapping to identities).

## Licence

CDLA-Sharing-1.0, as on the source record (Pennsieve: "Community Data License Agreement – Sharing"; DataCite rightsList: Community
Data License Agreement Sharing 1.0, cdla-sharing-1.0). The age/sex values copied from ds004100 are CC0 there.

## Ethics

Verbatim from the article (Shi et al. 2024, Materials and methods, Patient information): "iEEG and imaging data collection for
research was approved by the Institutional Review Boards of the Hospital of the University of Pennsylvania (HUP) and Medical
University of South Carolina (MUSC)."
