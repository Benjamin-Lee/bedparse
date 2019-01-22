---
title: 'Bedparse: feature extraction from BED files'
tags:
  - Python
  - Bioinformatics
  - Genomics
  - BED format
authors:
  - name: Tommaso Leonardi
    orcid: 0000-0002-4449-1863
    affiliation: "1, 2"
affiliations:
 - name: The Gurdon Institute, University of Cambridge, Tennis Court Road, Cambridge CB2 1QN, UK
   index: 1
 - name: Center for Genomic Science IIT@SEMM, Istituto Italiano di Tecnologia (IIT), Via Adamello 16, 20139 Milan, Italy
   index: 2
date: 22 January 2019
bibliography: paper.bib
---

# Summary
``Bedparse`` is a python module and CLI tool to extract features from genome annotation files in BED (Browser Extensible Data) format.
The BED format is a plaintext file format commonly used in bioinformatics to represent genomic features: each line in the file corresponds to a genomic feature (e.g. a gene, transcript, peak, regulatory region, etc.) and consists of up to 12 tab-separated fields that define its genomic coordinates and exon-intron structure. This format is also commonly used to graphically visualise genomic features with genome browser softwares, and is one of the standard formats used by the UCSC Genome Browser [@ucsc2002] and the Ensembl Genome Browser [@ensembl2018]. 
One of the major advantages of the BED format over many of its alternatives is that each line includes all the information required to define an individual gene/transcript model. This allows to perform most operations on BED files as part of unix pipes, for example using GNU awk one-liners or small custom scripts. This _ad-hoc_ approach, albeit usually simple and effective, often leads to repetition and/or code duplication and can be prone to errors, bugs or typos not always easy to detect.

``Bedparse`` aims to simplify and standardise many of the operations and feature-extractions commonly done on BED files by adhering to the UNIX philosophy of doing one thing and doing it well. Despite the simplicity of many of its functions, bedparse is thouroughly and rigourously tested through an automated test suit to ensure the accuracy and correctness of the results. Additionally, bedparse performs syntax validation checks on the input BED files and warns the user in case of inconsistencies or malformed files.

``Bedparse`` implements the following functions:
* Filtering of transcripts based on annotations
* Joining of annotation files based on transcript names
* Promoter reporting
* Intron reporting
* CDS reporting
* UTR reporting 

In addition to the feature-extraction functions reported above, ``bedparse`` also provides three format conversion tools:
* _convertChr_ implements an internal dictionary that allows conversion of human and mouse chromosome names (including patches) between the two most widely used formats, i.e. the Ensembl and the UCSC naming schemes.
* _gtf2bed_ allows converting Ensembl/Gencode Gene Transfer Format (GTF) files into BED format, with options to specify extra fields to add after column 12.
* _bed12tobed6_ converts BED12 files to the BED6 format.

Internally, ``bedparse`` implements a _bedline_ class that performs several checks on each BED field in order to ensure the correctness of the format, and implements methods that performs the functions listed above. This type of design allows ``bedparse`` to be either imported by other projects as a python module or to be used as a standalone tool through its command line interface.

In conclusion, ``bedparse`` is a light, versatile and portable tool developed using good programming practices and a test-driven development approach. Its use as part of bioinformatic pipelines will contribute to speeding up development time and preventing bugs.

``Bedparse`` is open-source and released under the MIT Licence. The source code is hosted on Github, and releases are automatically tested using Travis CI and archived on Zenodo.

# References