This article assumes you already have a RAP project and that your project has UKB data dispensed to it. If you have not yet completed these steps, please refer to the article [Getting started with a RAP project](02-Getting-started-with-a-RAP-project.md) first.

There three main ways to access phenotype data on RAP:
1. Exporting relevant data fields to a .csv/.tsv file
2. Creating a "View" with the desired participants and data fields, then using that view as input to an app on DNANexus.
3. Via Apache Spark, either directly or through relevant tools in a language such as Python (this option is mostly for advanced users)

### Exporting data to a .csv/.tsv file using Table Exporter via the web interface
FIXME: Add this

### Extracting data to a .csv/.tsv file using Table Exporter via the command line interface

1. Get the project ID for your project, and the record ID for the dataset you want to extract variables from. To get these:
   * The project ID will look like "project-abc123" where abc123 is a long string of random characters. To find your project ID, run `dx find projects`
   * The record ID will look like "record-abc123" where abc123 is a long string of random characters. To find the record ID for your desired dataset, run `dx find data --class record`
2. Make a list of fields/variables that you want to extract. Most variables will start with "p" and then some numbers, eg. p31 is sex and p22189 is Townsend Deprivation Index. Your list should be a file with one variable ID per row. There are at least three ways to find variable IDs:
   * Get the variable IDs from the UK Biobank data showcase. You will need to add "p" to the beginning of IDs you find there.
   * Get full details of available variables for your dataset using the command `dx extract_dataset project-abc123:record-abc123 -ddd --delimiter "\t"`. If this command succeeds, it will write files containing information about available variables to the directory you are in on your local computer (this is OK, these files contain no participant information). Look for a file ending in `.dataset.data_dictionary.tsv` and look for variable names like "p22189" in the second column of this file.
   * Get less-detailed variable information for your dataset using the command `dx extract_dataset project-abc123:record-abc123 --list-fields --entities participant > field-list.txt`. This file will contain IDs like `participant.p6152_i0` which you can shorten to just `p6152` (or you can keep the _i0 part if you really do just want the first instance)

### Creating and using a "View"
FIXME: Add this

### Links to documentation for Apache Spark
FIXME: Add these
