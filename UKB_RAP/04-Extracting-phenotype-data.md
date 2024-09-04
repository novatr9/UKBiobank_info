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
4. Run a Table Exporter job using the following command: `dx run table-exporter --destination /path/for/output/ -idataset_or_cohort_or_dashboard=record-abc123 -ioutput=output_file_start -ioutput_format=TSV -icoding_option=RAW -iheader_style=FIELD-NAME -ientity=participant -ifield_names_file_txt=extract-vars.txt
`
   * FIXME: Add dx run options to run the job with the cheapest possible instance and priority
   * `--destination` says where to output your extracted data. It can be `project-abc123:/` for the /  directory of your project, or something else like `/extracted_data/` if you have created a folder named "extracted_data" in your project and want to put your data there.
     * Including the `project-abc123:` part is optional in most circumstances, you can just write `/extracted_data/`.
     * You can also leave out the `--destination` option entirely if you use `dx cd` to get to your desired output directory before you submit your job.
   * `-ioutput=output_file_start` is the first part of your filename (before the .tsv). So `-ioutput=test` would lead to the creation of a file test.tsv
   * `-ifield_names_file_txt=extract-vars.txt` should point to the file with the list of variables to extract.
   * When an option begins with `-i`, that option is passed to the Table Exporter app, eg. `-ioutput_format=TSV` passes Table Exporter the option `output_format=TSV`. When an option doesn't begin with `-i` (like `--destination`) then it as option to the `dx run` command and not the Table Exporter app itself.

### Creating and using a "View"
FIXME: Add this

### Links to documentation for Apache Spark
FIXME: Add these

### Making a list of fields/variables to extract

Several of the methods above use a list of variables to extract. This list of variables should be a file with one variable per row, like this:
```
eid
p31
p680_i0
p22189
```

The general format of a variable name is either `p12345` (for variables without instances) or `p12345_i0` (for variables with instances). An instance is a repeat measurement of the variable at a later UK Biobank visit - all participants have instance 0 (baseline/intake) some also have other instances for things like an MRI visit or a follow-up visit.
* If a variable has instances, you must specify each instance that you want, eg. `p680_i0` `p680_i1` etc. Just specifying `p680` will cause your data extraction to fail.
* If a variable's only instance is baseline/intake, you must write its name without `_i0` - for these variables, writing `p31_i0` will cause your data extraction to fail.

There are at least two ways to find variable IDs for making your list:
* Get the variable IDs from the UK Biobank data showcase. You will need to add "p" to the beginning of the numeric variable IDs you find there. For variables with instances, you will need to add instance on the end, eg. `p680_i0`.
* Get variable information for your dataset using the command `dx extract_dataset project-abc123:record-abc123 --list-fields --entities participant > field-descrip.txt`. This file will contain IDs like `participant.p680_i0` - just remove the `participant.` part from the beginning and they'll be ready to add to your list.
  * This command is a good way to check which variables need an instance in their names.
