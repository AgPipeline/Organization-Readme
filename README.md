<!-- NOTES: 1) This document is intended to be a quick(ish) read. To this end, please don't document items that are better kept in a file, such as the pylint.rc file, just provide a link/location - especially if the file format allows self documentation! 2) Each sentence is to be on its own line, do not put two sentences on the same line. -->
# Contributing
This repository contains information on how to contribute to this GitHub organization in the form of this README.md, other files, and documents and links.

This document should be considered a work in progress and will change as new standards and technologies emerge.
Please be sure to read this documentation on how to contribute so that we all can have a great experience!

Feel free to ask questions about anything in this document using [issues](https://github.com/AgPipeline/computing-pipeline/issues).

## Additional reading
Technical details on contributing can be found in the [computing-pipeline](https://github.com/AgPipeline/computing-pipeline) repo's [CONTRIBUTING.md](https://github.com/AgPipeline/computing-pipeline/blob/master/.github/CONTRIBUTING.md) file.

# History
This organization is a fork of the [TERRA REF](https://github.com/terraref) project (and might be thought of as TERRA REF 2.0).
The TERRA REF project was built up around the world's [largest mobile agricultural gantry sensing platform](https://terraref.org/).
As that project was wound down, ownership of the gantry was passed to the [University of Arizona (UA)](https://www.arizona.edu/).
This organization arose out of the need to adapt the processing pipeline to the UA [CyVerse](https://cyverse.org/) environment, and to extend it to support sensors mounted on drones, tractors, and carts.

As part of the technology associated with the gantry ownership transfer, a rework on the existing code was required.
Given the extent of the changes required and desired, this GitHub organization was created.
Some of the primary factors requiring changes are reduced support personell, different infrastructure, and leveraging HPC.
Some of the desired changes are simplifying transfer of technology (making it easy to run in alternate environments), standardization of workflow processes (encapsulated as 'extractors'), making contributions of scientific algorithms as easy as possible, and dynamic workflows.

# Reaching Goals
To reach the goals of providing a stable, flexible workflow that minimizes customization and easing the development of scientific algorithms, we are implementing constraints on how to contribute to the organization, and documenting our standards.

# Repositories
The organization of repositories for organizations/projects this size can be an issue.
One important way of managing this is to use appropriate naming conventions so that repos are easy to find.
Another aspect is to keep a repository's meaning clear; for example. don't combine administrative scripts with product code.

How best to structure a repository is very dependent upon what is being developed.
A good way to structure a repo is to place everything needed for a solution within that repository.
For example, place a Dockerfile used to build an image in the repo and not in a separate repo.
If there are multiple Dockerfiles for a single repo, you may consider putting them in a folder named "dockerfiles", but then again maybe not.

Keeping repos as single purpose as possible is also encouraged.
This does not prevent major complexity within a repo.

In the end, use your best judgement, don't be afraid to reorganize, and ask if you have any questions!

# Branches
There are several ways of handling branching in repositories of which we've chosen one.

For any repositories containing code, tests, scripts, and other executables we use a [master/develop methodology](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows) with other branches for feature/issue development.
We also support pull requests from other organizations as well as personal repos.

For all other repositories, we strongly recommend using master/develop branching as above.
Please use a methodology that makes sense for your project and document the rules in the repo's README.

# Pull Requests
When a branch is ready to be merged, a Pull Request is made.
Pull Requests must be reviewed to be accepted for merging, and a successful test using CI (see below) has to be done.
Please be sure to configure your repository for these requirements.

# Merging
To promote frequent commits, branches are to be squashed when merged (their history removed).
This  is done to promote the commit of even very minor changes, without cluttering the history of the main branches (master and develop).

A potential problem with this approach to merging is the loss meaningful of history.
By appropriate commenting and other documentation, this problem can be avoided.

# Coding Standards
Coding standards are most efective when they don't cause a large burden for developers.
If coding standards can be applied through the use of tools, that is the recommended approach to take.

## Python
All Python code must support Python 3.7 or later.

In the root of this repo there's a `pylint.rc` file.
As can be guessed by the name of this file, it's expected that all python scripts will pass a run of [pylint](https://www.pylint.org/) with a score of 10.0.
Exceptions to this are allowed as long as they are documented to show that it's deliberate and justified.
Copy the `pylint.rc` file to your repo to make it easy to use in for your work.

# Testing
All code needs to have test cases, with the exception of the TERRA REF code which is being grandfathered in.

# Continuous Integration (CI)
All code in repositories must have Continuous Integration (CI) enabled.
Other repositories can also have CI enabled if it makes sense for them.
The CI steps need to perform code conformance tests (such as passing `pylint`), unit tests, build tests, and functional tests.
It's desireable that these tests are performed on the final product(s) of the repo; against newly built docker images for exanple.
