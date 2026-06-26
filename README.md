# Gender_Stereotyping_Artists

This repository contains codes to reproduce the results of the research paper "X". I have used Python to collect and clean data, and both Python and RStudio for text analysis. I have mentioned the runtime of each computationally expensive codes on top of it and the reproduction of the research requires following the file sequence in the `01_notebooks_&_py_files` folder. 


## Workflow

```mermaid
flowchart LR

    A[notebooks/01_data_collection.ipynb]
    S[src/*.py]
    M[(model)]
    D[(data)]
    C[[Hand Coding]]
    B[notebooks/02_data_preparation.ipynb]
    SA[notebooks/03_sentiment_analysis.ipynb]
    STM[notebooks/04_stm.rmd]
    R[notebooks/05_regressions.do]
    O[(results)]

    A -->|Data collection scripts| S
    S -->|Downloads YouTube comments| D

    D -->|Unsure videos| C
    C -->|Gender labeled and clickbait removed| D

    B -->|Preprocessing scripts| S
    B -->|Transliteration model| M
    D -->|Raw comments| B
    B -->|cleaned, translated, transliterated| D

    D -->|Prepared corpus| SA
    SA -->|VADER outputs| O

    D -->|Prepared corpus| STM
    STM -->|STM model and plots| O

    D -->|corpus with outputs of STM and VADER| R
    R -->|Regression tables and statistics| O
