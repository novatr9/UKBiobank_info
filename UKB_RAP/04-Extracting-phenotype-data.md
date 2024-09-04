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
2. Make a list of fields/variables that you want to extract. See the bottom of this page for details on how to do that.
3. Upload your list of variables to extract back to UKB RAP with the command `dx upload extract-vars.txt` where extract-vars.txt is whatever name you gave your list of variables to extract.
4. Run a Table Exporter job using the following command: `dx run table-exporter -idataset_or_cohort_or_dashboard=project-abc123:record-abc123 -ioutput=your_output_file_with_no_suffix -ioutput_format=TSV -icoding_option=RAW -iheader_style=UKB-FORMAT -ientity=participant -ifield_names_file_txt=extract-vars.txt`
   * FIXME: Add dx run options to run the job with the cheapest possible instance and priority

### Creating and using a "View"
FIXME: Add this

### Links to documentation for Apache Spark
FIXME: Add these

### Making a list of fields/variables to extract

Several of the methods above use a list of variables to extract. This list of variables should be a file with one variable per row, like this:
```
eid
31
6152
22189
```

If you want to specify a particular instance number of a variable (instance numbers refers to visits, with 0 being the baseline/intake appointment), you can write the variable name as 12345-0.

There are at least three ways to find variable IDs for making your list:
* Get the variable IDs from the UK Biobank data showcase. You will need to add "p" to the beginning of the numeric variable IDs you find there.
* Get full details of available variables for your dataset using the command `dx extract_dataset project-abc123:record-abc123 -ddd --delimiter "\t"`. If this command succeeds, it will write files containing information about available variables to the directory you are in on your local computer (this is OK, these files contain no participant information). Look for a file ending in `.dataset.data_dictionary.tsv` and look for variable names like "p22189" in the second column of this file (remove the "p" before adding the variable to your list).
* Get less-detailed variable information for your dataset using the command `dx extract_dataset project-abc123:record-abc123 --list-fields --entities participant > field-descrip.txt`. This file will contain IDs like `participant.p6152_i0` which you can rewrite as `6152` (to get all instances) or `6152-0` (to get values of this variable for the baseline instance)
