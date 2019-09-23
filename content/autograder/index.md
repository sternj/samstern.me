+++
title = "AutoGrader"
date = 2019-09-18
+++

### [Github](https://github.com/capstone-auto-grader)

AutoGrader is a full-stack solution simplifying the lives of grading TAs at Brandeis. It works with existing data in Moodle and provides tools for distributing grading assignments and aggregating grades. 

## Architecture

AutoGrader consists of two services— the AutoGrader webserver, which stores project and grade information and provides an interface for grading TAs, and the Grading API, which tasks containers with grading, validation, and recombination jobs. The Grading API runs jobs asynchronously using Rails ActiveJobs. 

![Autograder Architecture Diagram](/images/autograder.png)

## Modes of operation

AutoGrader can be used as either a submission grouper, as a testing/sanitizing suite, and as a wrapper around the MOSS cheat detection system.

### Grouping

AutoGrader assigns students' submissions to grading TAs automatically and distributes their partitions in organized archive files. Grading TAs can provide a grade and comments, which are aggregated in a grading worksheet that can be uploaded to Moodle. 

### Testing

Course administrators can provide a test suite to be run against each student's submission. The test suite and all relevant auxiliary files will be put in each student's project directory (overwriting previous files), the tests will be run, and the results will be made visible to each student's grading TA. Additionally, the TAs will be provided their students' submissions with the full test suite and all auxiliary files.

### Cheat detection

AutoGrader structures submissions to be uploaded to MOSS and provides the course administrator a link to the site on the MOSS website. If it expires, the course administrator can trigger a regrade. 