# Extracting images to be annotated from Puhti

## A very short introduction to Puhti and CSC

### Background

[Puhti](https://docs.csc.fi/computing/systems-puhti/) is a supercomputer hosted by [CSC](https://www.csc.fi/en/) - the Finnish IT Center for Science. Puhti, as well as most other resources and services provided by CSC, are free to use for research purposes. In order to use the resources, a research group needs to create a project. Each project is given a specific amount of billing units. Using the CSC resources consumes these billing units and thus they are essentially a way to regulate the amount of resources a specific CSC project can use. The DRYTREE project has two CSC projects:

`Project number 2008436` - A project for managing data related to the DRYTREE project

`Project number 2004205` - A project for running computations related to the DRYTREE project

### The Puhti filesystem

There are three main disk areas in Puhti:

`home` - The home directory of a specific Puhti user. This is the default directory you end up in when you log into Puhti. Only you have access to this directory

`projappl` - A project-specific directory for storing code related to the project. The directory can be accessed by all project members.

`scratch` - A project-specific directory for storing project-related data that is constantly used. The directory can be accessed by all project members and is supposed to be only used as a short-term data storage. CSC has other services, such as [Allas](https://docs.csc.fi/data/Allas/) for long-term data storage. 


