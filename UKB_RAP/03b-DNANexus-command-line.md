UKB RAP is based on the DNANexus platform. You can use the DNANexus command line utilities to perform many tasks in UKB RAP.

This page has instructions for *using* the command line tools. Before you use them, you will need to install them as described on the page [Installing the command line tools](Installing-the-command-line-tools.md).

### Useful documentation for the command line tools

Quickstart guide: https://documentation.dnanexus.com/getting-started/cli-quickstart<br/>
Full command reference: https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities<br/>
Type `dx help all` to see one-line summaries of all available dx commands, or `dx help commandname` to see more detailed documentation for a specific command.

### Signing in using the command line tools

To sign in, run the command `dx login`, and enter the same username and password you first created when registering your RAP/DNANexus account. You will not see any change in your command prompt (the way you would when you ssh to something) because you have not established a persistent connection to a remote system. The only thing that happens when you log in is that you have authenticated yourself, so now when you run other "dx" commands (from your local system) they will have permission to establish as-needed connections to RAP/DNANexus in order to carry out your commands.

When you log in, you will be shown a list of projects you have access to (if there are any), and it may automatically set one of them as your current project.

If you want to sign out when you are finished, you can run the command `dx logout`. If you are the only person who uses your computer, you can choose to stay authenticated for up to 30 days instead of logging out.

### Viewing and selecting projects with the command line tools

To see a list of projects you have "contribute" or higher access to, use the command `dx find projects`. To make one of those projects your current active project for other dx commands, use the command `dx select projectname` (where projectname is the name of your project). You can also use the command `dx select` with no other options to see a list of projects you have access to and be prompted to select one. If you only have access to one project, `dx select` will set that as your active project automatically.

You can also use the command `dx select --level VIEW` to see projects you have read-only access to, or `dx select --public` to see projects that are publicly available (such as reference datasets).

### Using the command line tools to manage data

Once you have selected a project as your current project, you can use "dx" with basic Linux commands (`dx ls` `dx cd` `dx mv` etc.) to manage files within your project.

To copy data between two projects you have access to, you can include the name of the non-active project in the path given to the `dx cp` command, adding a `:` before the `/` to indicate that you are referring to another project (and not a directory with that name within your project).<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For example: `dx cp "Apollo Reference Data - AWS UKB RAP (London):/gnomAD Annotation Data/" gnomad`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;would copy gnomAD annotation data from the public project "Apollo Reference Data - AWS UKB RAP (London)"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;to a directory called "gnomad" in your current active project.<br/>
**Note:** You can only do this between two projects in the same AWS region. For UKB RAP, this means you can only copy data to/from other projects with region (London). All UKB RAP projects have region (London), even though they do not say (London) in their name.

To copy a small amount of data from your local system to your current active project, you can use the `dx upload` command. To copy a larger amount of data, you will need to install and use the Upload Agent. (Details for the Upload Agent: https://documentation.dnanexus.com/user/objects/uploading-and-downloading-files/batch/upload-agent )

To copy data from your current active project to your local system, you can use the `dx download` command. **Please do not attempt to download individual-level data about UKB participants, this is not allowed.**

### Using the command line tools to manage projects
FIXME: Add this
