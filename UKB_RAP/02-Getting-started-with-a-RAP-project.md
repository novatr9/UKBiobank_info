### Terminology overview

The main unit of organization on RAP is a "project". Projects are where data is kept, and what jobs are run under. Users are given access to projects so they can use/store data and run jobs. Each project is linked to a billing account, which it will charge for data storage and for running jobs. Multiple projects can be linked to the same billing account.

A UK Biobank project and a RAP project are two different things. A UK Biobank project relates to applying for and being approved to use UK Biobank data (IBG PIs have already done this). A RAP project is a workspace for your data and results. A RAP project must be linked to an approved UK Biobank project, but numerous RAP projects can exist and be linked to the same UK Biobank project.

### Joining a project on UKB RAP

If you are collaborating with someone who has already set up a UKB RAP project for your collaboration, you do not need to create your own RAP project.

Please be aware that until we have billing accounts set up for PIs/labs, anything you run will be billed to the project owner's personal UKB RAP balance, so please make sure that they are OK with you sharing their RAP project.

There are three roles possible on RAP projects - "Contributor" "Admin" and "Member". (**FIXME:** I have not yet figured out how these are set/managed, it may be through UK Biobank AMS or it may just not show anything yet since I'm the only active user. Please update this documentation if you figure it out before I do.)

### Creating a project on UKB RAP

We do not yet have any shared lab billing information set up on RAP - for now when you create your project you will need to use your personal 40 GBP starting balance that you get automatically as a new user of UKB RAP.

To create a RAP project:
1. Access the projects page at https://ukbiobank.dnanexus.com/panx/projects or by going to the "Projects" menu in the top-left corner and selecting "All Projects".
2. In the top right corner, click the teal button that says "+New Project"
3. Enter the following information:
   * A name for the project
   * The ID number of your approved UK Biobank project (if you are under Matt's UKB project, the ID is 16651)<br/>
     **NOTE:** Your UK Biobank AMS account must be listed as an approved collaborator on a UKB project (talk to
     Matt or Katerina if you need to be approved on Matt's project) and must be linked to your RAP account
     before you can receive data under the project ID. See our documentation on RAP signup instructions
     for more details on linking your accounts.
   * Select data types to dispense (dispense means "make available under your RAP project"). "Tabular data" means phenotype data, "bulk data" means larger data such as genotype and imaging data.
   * Under "billed to", set your personal RAP billing account, which has a starting balance of 40 GBP. (This document will eventually be updated with information about a billing account at the lab/PI level once these exist, but for now we are all just experimenting with the system using our personal starting balances.)
4. Your project will be created immediately, but you may have to wait several hours for data to be dispensed (even
   if you have not requested bulk data). You can check the status of your project under the "All Projects" page from
   step 1, when data has been dispensed your project will show a status of "Ready".                                                                                                 
