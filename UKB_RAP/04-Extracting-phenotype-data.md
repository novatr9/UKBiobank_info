This article assumes you already have a RAP project and that your project has UKB data dispensed to it. If you have not yet completed these steps, please refer to the article "02-Getting-started-with-a-RAP-project.txt" first.

There three main ways to access phenotype data on RAP:
1. Exporting relevant data fields to a .csv/.tsv file, then either:
   * Importing the data into the environment used for your analysis (recommended for most datasets)
   * Accessing the data via the DNANexus API (may be necessary for very large datasets)
2. Creating a "View" with the desired participants and data fields, then using that view as input to an app on DNANexus.
3. Via Apache Spark, either directly or through relevant tools in a language such as Python (this option is mostly for advanced users)

### Exporting data to a .csv/.tsv file

### Using data that has been exported to a .csv/.tsv file
