# Extracting images to be annotated from Puhti

## A very short introduction to Puhti and CSC

### Background

[Puhti](https://docs.csc.fi/computing/systems-puhti/) is a supercomputer hosted by [CSC](https://www.csc.fi/en/) - the Finnish IT Center for Science. Puhti, as well as most other resources and services provided by CSC, are free to use for research purposes. In order to use the resources, a research group needs to create a project. Each project is given a specific amount of billing units. Using the CSC resources consumes these billing units and thus they are essentially a way to regulate the amount of resources a specific CSC project can use. The DRYTREE project has two CSC projects:

*Project number 2008436* - A project for managing data related to the project

*Project number 2004205* - A project for running computations related to the project

### The Puhti filesystem

There are three main disk areas in Puhti:

*home* - The home directory of a specific Puhti user. This is the default directory you end up in when you log into Puhti. 
Each Puhti user has a user-specific home directory. This is the the directory you end up in when you log into Puhti

For each CSC project, there are two project-specific directories in the Puhti filesystem


