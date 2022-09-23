# Framework 

## Introduction

Any trusted AI T&E (TODO: define) must consider the problems of deployment in mission ciritical applications in addition to the usual measurment of success based on measurment of training accuracy.
The T&E Framework Infrastructure project provides a framework for connecting the various components and toolboxes being developed for the Trusted AI project together into a single coherent system.

The system provides standardized methods for storage and version control of code, data and documentation.
There is a minimum viable vocabulary to describe experiments, as well as metadata and storage criterion for model/data outputs such as Neural Network weights.

Preference is given to Open Source Software and Tools that can either be integrated into the Framework or modified by our software development teams with possible contribution back to their parent project.

## Overview

The core of the framework is the version control system [Git] and the storage overlay provided by the [Data Version Control] (DVC) project.
All model code, data preperation code, and training workflows are tracked in as a Git Repository.
Training data, generated models, and analytics are tracked by DVC.
DVC provides a way to track file versions in Git, but store the contents elseware.
This is useful since training data and models tend to be large and numerious, both things that become a liability when stored directly in a Git repository.

[git]: https://git-scm.com/
[Data Version Control]: https://dvc.org/









## Projects
* [Maintenance Operators Ontology](https://nd-crane.github.io/moo)
* [Paper Analytical Devices](https://nd-crane.github.io/paper-analytical-devices)





