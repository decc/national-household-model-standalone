# Synopsis
This repository holds the projects necessary to build the National Household Model Standalone (IDE), the IDE utilises the open-source [Eclipse] (http://www.eclipse.org/) IDE and adds customisation to allow the editing of scenarios (a scripting language for describing simulation events for the National Household Model), importing housing stocks from structured CSV files and running simulations using the model. The implementation of the model is available from a separate repository detailed in External Project Dependencies.

More information on using the model can be found both [National Household Model Documentation] (https://github.com/cse-bristol/national-household-model-documentation/releases/tag/Current) and within the internal help menus of the Standalone.

# Installation
To build the Standalone project locally both the OSGI Bundles,  [National Household Model] (https://github.com/cse-bristol/national-household-model-core-components) and  [National Household Model Documentation] (https://github.com/cse-bristol/national-household-model-documentation) need to be compiled as jars and installed within a local Maven repository.

## OSGI Bundles
OSGI is the way customisations can be added to the Eclipse IDE, typically these should be compiled and hosted in a P2 repository, the repository location should then be defined in the repositories element of the IDE pom file.

### API - nhm-api-bundle
Defines the Application Programming Interface for an NHM Bundle. This is a Gradle project and should be configured to push the generated p2 bundle into a p2 repository.

### IMPL - nhn-bundle-impl
This is an implementation of the API bundle, the project will need to be updated when the IDE needs to include new commits to [National Household Model] (https://github.com/cse-bristol/national-household-model-core-components) or [National Household Model Documentation] (https://github.com/cse-bristol/national-household-model-documentation). Again this is a Gradle project and has the same installation requirements as the API Bundle. See the Gradle build file for current dependencies.

## Standalone - Eclipse IDE
Uses Maven(3) to build the project.

This is the customised Eclipse IDE, in order to build correctly it depends on API Bundle, IMPL Bundle and [National Household Model Documentation] (https://github.com/cse-bristol/national-household-model-documentation). The Model and Documentation projects should be either installed in a local or remote repository, the Bundles should be available in a local or remote P2 repository. The locations of remote respositories can be configured in the repositories element of the build file (pom.xml).

Creates Standalone binaries for the linux (32 and 64 bit), Windows (32/64 bit) and Mac OSX Cocoa.

In order to sign the created application you will need to 'sign' the build with a secure key, the location of the keystore and passphrase can be configured in your maven settings file. See the maven-jarsigner-plugin in the pom file. 

## External Project Dependencies
1. [National Household Model] (https://github.com/cse-bristol/national-household-model-core-components) - This is the model part of the National House Hold model.
2. [National Household Model Documentation] (https://github.com/cse-bristol/national-household-model-documentation) - Provides the help/reference guide to the NHM within the IDE.

## Binaries - Compiled Executables of the Standalone IDE
If you wish to simply install a run a version of the NHM Standalone IDE then please download the latest binary from [here](https://github.com/cse-bristol/national-household-model-standalone/releases/tag/Current).

In order to run a simulation you will also need to import a housing stock, this is accomplished by creating a series of structued csv files wrapped in a zip file. Details on how the structure of these files are included in the [National Household Model Documentation] (https://github.com/cse-bristol/national-household-model-documentation).

There is also project written in R that can create these structure stock files from specific data-sets, details on this can be found [here](https://github.com/cse-bristol/national-household-model-stock-files-creator).

# License
[Open Government License] (http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/)
