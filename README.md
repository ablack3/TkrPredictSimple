Predicting 90-day mortality following total knee replacement
======================
<img src="https://img.shields.io/badge/Study%20Status-Started-blue.svg" alt="Study Status: Started">

- Analytics use case(s): **Patient-Level Prediction**
- Study type: **Clinical Application**
- Tags: **Study-a-thon, COVID-19**
- Study lead: **Jenna Reps, Ross Williams**
- Study lead forums tag: **[jreps](https://forums.ohdsi.org/u/jreps), [RossW](https://forums.ohdsi.org/u/RossW),**
- Study start date: **Dec 16, 2018**
- Study end date: **-**
- Protocol: **[Link](https://github.com/OHDSI/StudyProtocols/blob/master/UkaTkaSafetyEffectiveness/documents/OHDSI%20Oxford%20PLE%20Protocol%2030dec2018.docx)**
- Publications: **-**
- Results explorer: [Link](https://data.ohdsi.org/TKROutcomesExplorer/)

The objective of this study is to develop and validate various patient-level prediction models for total knee replacement patients. 


Introduction
============
This repo contains the simple models needed for validation of the Oxford Ehden study-athon simple models to predict mortality following a total knee replacement

Features
========
  - Validates the full models developed in Thin and OptumDod as well as a user designed simple and a data driven simple developed in optumDod
  
  - Included in the package are 4 models they are:
    - Analysis_1: the full mdoel developed in optumDod
    - Analysis_1001: the simple model using user defined inputs
    - Analysis_1002: the simple model using data driven development methods (high penalisation)
    - Analysis_2: the full model developed on THIN

Technology
==========
  oxfordKneeValidation is an R package.

System Requirements
===================
  Requires R (version 3.3.0 or higher).

Dependencies
============
  * PatientLevelPrediction

Getting Started
===============
  1. In R, use the following commands to run the study:

  ```r
library(oxfordKneeValidation)
# USER INPUTS
#=======================
# Specify where the temporary files (used by the ff package) will be created:
options(andromedatempdir = "S://temp//tempandromeda")

# The folder where the study intermediate and result files will be written:
outputFolder <- "./tkrSimpleResults"

dbms <-
user <-
pw <-
server <-
port <-

connectionDetails <- DatabaseConnector::createConnectionDetails(dbms = dbms,
                                                                server = server,
                                                                user = user,
                                                                password = pw,
                                                                port = port)
# Add the database containing the OMOP CDM data
cdmDatabaseSchema <- ''
# Add the name of database containing the OMOP CDM data
cdmDatabaseName <- ''

# Add a database with read/write access as this is where the cohorts will be generated
cohortDatabaseSchema <- ''
oracleTempSchema <- NULL


# table name where the cohorts will be generated
cohortTable <- 'tkrSimpleTest'

#============== Pick Study Parts To Run: ===========
createCohorts = FALSE
predictTkrSimple = TRUE
runValidation = TRUE

packageResults = TRUE

minCellCount <- 5
sampleSize <- NULL


#============== Pick T and O cohorts ===========

# [option 1] use default cohorts
usePackageCohorts <- TRUE
newTargetCohortId <- NULL
newOutcomeCohortId <- NULL
newCohortDatabaseSchema <- NULL
newCohortTable <- NULL

#=======================
# TAR settings - recommended to not edit
#=======================
riskWindowStart <- 0
startAnchor <- 'cohort start'
riskWindowEnd <- 90
endAnchor <- 'cohort start'
firstExposureOnly <- F
removeSubjectsWithPriorOutcome <- F
priorOutcomeLookback <- 99999
requireTimeAtRisk <- F
minTimeAtRisk <- 1
includeAllOutcomes <- T

execute(connectionDetails = connectionDetails,
        usePackageCohorts = usePackageCohorts,
        newTargetCohortId = newTargetCohortId,
        newOutcomeCohortId = newOutcomeCohortId,
        newCohortDatabaseSchema = newCohortDatabaseSchema,
        newCohortTable = newCohortTable,
        cdmDatabaseSchema = cdmDatabaseSchema,
        cdmDatabaseName = cdmDatabaseName,
        cohortDatabaseSchema = cohortDatabaseSchema,
        cohortTable = cohortTable,
        sampleSize = sampleSize,
        riskWindowStart = riskWindowStart,
        startAnchor = startAnchor,
        riskWindowEnd = riskWindowEnd,
        endAnchor = endAnchor,
        firstExposureOnly = firstExposureOnly,
        removeSubjectsWithPriorOutcome = removeSubjectsWithPriorOutcome,
        priorOutcomeLookback = priorOutcomeLookback,
        requireTimeAtRisk = requireTimeAtRisk,
        minTimeAtRisk = minTimeAtRisk,
        includeAllOutcomes = includeAllOutcomes,
        outputFolder = outputFolder,
        createCohorts = createCohorts,
        predictTkrSimple = predictTkrSimple,
        runValidation = runValidation,
        packageResults = packageResults,
        minCellCount = minCellCount,
        verbosity = "INFO",
        cdmVersion = 5)


```

License
=======
  oxfordKneeValidation is licensed under Apache License 2.0

Development
===========
  oxfordKneeValidation is being developed in R Studio.
