# Data access and repository boundaries

MIMIC-IV and MIMIC-IV-Note are credentialed datasets distributed through PhysioNet. Their source tables, clinical notes and restricted derivatives are not included in this repository.

The public repository intentionally excludes:

- raw or preprocessed discharge-summary text;
- note, admission and patient identifiers;
- annotation workbooks containing clinical text;
- mention-level exports that reproduce source passages;
- locally generated datasets and model outputs containing restricted content.

Authorised users must obtain the data independently from PhysioNet, comply with the applicable data-use agreement, and configure the local project paths before running the notebooks.
