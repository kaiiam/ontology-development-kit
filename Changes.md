# v1.2

**MAJOR OVERHAUL OF FRAMEWORK**

This release sees the introduction of project.yaml files (see
[examples/](examples)). Although command line passing of parameters is
still supported, the use of a project file is strongly encouraged.

Previously the following commands may be have been passed: `-c -d pato -d cl -d ro -t my-ontology myont`

Now you can use a yaml file:

```
id: myont
title: my ontology
import_group:
  products:
   - id: ro
   - id: cl
   - id: pato
```

## Changes for Users

 * project.yaml files can be passed instead of command line settings
 * Docker container can now be executed anywhere, no checkout required
 * Added [README-developers.md](README-developers.md) for ODK developers
 * Docker container tracking ROBOT v1.2
 * Previously multiple dependencies: `-d ont1 ont2 ... ontN`, now `-d ont1 -id ont2 ... -d ontN`
 * New command line option `--source` to pass in an existing ontolgy-edit file

## Changes for ODK Developers

 * Dockerfile for odkfull now at root directory
 * Dockerfile now based on alpine
 * Perl script gone; new python script (Python3.6 required)
 * Uses Jinja2 templating system, including dynamic file templating

## Migration Guide

This will be complex BUT the new system will make future development easier.

You MAY want to wait for future incremental releases which will
include migration tools. But if you want to forge ahead, we recommend
creating a new repo and copying files across manually.

# v1.1.3

## Changes

 * fixing bug in which running seed-via-docker did not enter interactive mode when no arguments provided
 * added convenience wrapper scripts

## Migration guide

 * New .sh scripts in src/ontology can be directly copied across

# v1.1.2

## Changes

 * added interactive mode
 * added [DOSDP](https://github.com/INCATools/dead_simple_owl_design_patterns/blob/master/src/simple_pattern_tester.py) support

## Docker

 * [odkfull](https://hub.docker.com/r/obolibrary/odkfull/tags/) v1.1.2 includes robot 1.1.0

## Migration guide

This release adds a new template in the `src/patterns` folder. These can be copied across to an existing repo.

# v1.1.1

## Changes

Name of repo has changed to ontology-developer-kit

 * changing name of docker image to odk
 * Upgrade dosdp-tools to release 0.9.
 * Make docker commands workable on windows
 * Dockerize travis
 * Imports automatically generated
 * Added python dosdp checker to docker, fixes #55
 * use robot not owltools in all places

## Docker

odklite and odkfull 1.1.1 released. Note that new versions may be released independent of odk

 * robot pre-1.1.0
 * dosdp-tools 0.9

The docker release includes a pre-release of [robot 1.1.0](https://github.com/ontodev/robot/releases/tag/v1.1.0).
This is identical to 1.1.0, except for https://github.com/ontodev/robot/commit/928503b1303c139fc1cf4fc1939d64bda0f2ae30

## Migration guide

If you built your repo from a previous version of ODK, here is a rough guide to migrating:

 * Update your .travis.yml, in order to use Docker (optional but recommended)
 * change the name of the docker image to odkfull in your run.sh

# 1.1.0

 * Add a run.sh in the template for Docker
