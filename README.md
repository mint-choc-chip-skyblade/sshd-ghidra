# Ghidra Documentation for The Legend of Zelda: Skyward Sword HD

## ⚠️Update⚠️
**This repository is now defunct. Please refer to the following information for how to access The Legend of Zelda: Skyward Sword HD Ghidra server. This repository is being left for documentation purposes.**

Please note, this method of sharing project information is an unsuitable alternative to hosting a Ghidra server due to the loss of namespace information when creating a new project based on the xml files in this repository. **This method should be avoided for other projects.**

### [New Home](https://www.youtube.com/watch?v=EBhFHJMVfiI)
The reverse engineering effort for The Legend of Zelda: Skyward Sword HD is now hosted by the zeldaret team to facilitate a collaborative effort to document the disassembled code with the primary goal of creating [The Legend of Zelda: Skyward Sword HD Randomizer](https://github.com/mint-choc-chip-skyblade/sshd-rando).

You may be interest in looking at [The Legend of Zelda: Skyward Sword Randomizer](https://github.com/ssrando/ssrando), particularly its Discord server, as the SD version of the game is much further along in it's documentation efforts and easier to get started with than HD. Also, please see [The Legend of Zelda: Skyward Sword Decompliation](https://github.com/zeldaret/ss) project.

What follows is the documentation about how to setup the now defunct method of setting up Ghidra for working with the code for The Legend of Zelda: Skyward Sword HD. At the time of writing, we have updated to Ghidra 10.4 PUBLIC and will continue to update when possible. The following instructions are for Ghidra 10.3 PUBLIC and will not be updated.

## Table of Contents
* [Pre-requisites](https://github.com/mint-choc-chip-skyblade/sshd-ghidra#pre-requisites)
* [Setup](https://github.com/mint-choc-chip-skyblade/sshd-ghidra#setup)
* [Importing Shared Documentation](https://github.com/mint-choc-chip-skyblade/sshd-ghidra#importing-shared-documentation)
* [Contributing](https://github.com/mint-choc-chip-skyblade/sshd-ghidra#contributing)

## Pre-requisites

You will need:
* [Ghidra 10.3](https://github.com/NationalSecurityAgency/ghidra/releases/tag/Ghidra_10.3_build)
* [Ghidra-Switch-Loader](https://github.com/Adubbz/Ghidra-Switch-Loader)
    * Pre-built releases can be found at [StevensND's fork](https://github.com/StevensND/Ghidra-Switch-Loader/releases)
* ~1 hour of free time (+ the time needed to analyse the code files you wish
  to look at)
    * The approximate analysis times for each code file for The Legend of
      Zelda: Skyward Sword HD are:
        * `rtld    -> ~1-2   minutes`
        * `main    -> ~55-60 minutes`
        * `sdk     -> ~25-30 minutes`
        * `subsdk0 -> ~20-25 minutes`
        * `subsdk1 -> ~15-20 minutes`

## Setup

Make sure you have all the pre-requisites and that you have followed the
installation instructions for Ghidra-Switch-Loader.

### New Project

First, you will need to create a new Ghidra project. To do this, go to:

`File -> New Project...`

![The Ghidra File menu showing the "New Project" option.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/new-project.png?raw=true)

Next, select the `Non-Shared Project` type and click `Next >>`

![The Ghidra New Project "Select Project Type" window with the "Non-Shared Project" option selected.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/new-project-type.png?raw=true)

Finally, choose a location for the new Ghidra project to be stored and give it
a name. It is recommended that you choose a new directory to ensuer files
don't get lost.

![The Ghidra "Select Project Location" window with the "Project Directory" and "Project Name" fields filled appropriately.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/new-project-location.png?raw=true)

### Import Code Files

Next, you will need to import the files that you wish to work with into
Ghidra. The file of most interest is the `main` file as it contains the code
unique to The Legend of Zelda: Skyward Sword HD. It is one of six files in the
`exefs` directory of the game extract. All of these files are `.nso` files
except for `main.npdm`.

To import these code files, go to:

`File -> Import File...`

![The Ghidra "File" menu showing the "Import File" option.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/import.png?raw=true)

If you successfully installed Ghidra-Switch-Loader, Ghidra should
automatically detect that the code file you are importing is a `.nso` file and
the format and language should be filled out for you. If not, you will need to
set the `Format` field to `Nintendo Switch Binary` and the `Language` field to
`AARCH64:64:v8A:default`.

The `Destination Folder` field should be the directory that you chose for your
new Ghidra project and shouldn't need changing. The `Program Name` field will
default to the name of the code file you are importing. It is recommended to
keep this unchanged.

![The Ghidra Import window showing the "Format", "Language", "Destination Folder", and "Program Name" fields filled appropriately.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/import-format-and-language.png?raw=true)

### Analysis

You can now open the file you imported by double-clicking it. This will open
the `CodeBrowser` window. Once opened, you will be greeted with a popup window
asking if you wish to analyse your code file. Click `Yes`.

![The Ghidra "Analyze" popup window with the "Yes" option selected.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/analyse.png?raw=true)

The `Analysis Options` window will now open. It will contain a list of
`Analyzers` on the left and `Description` and `Options` information on the
right.

Click the `Select All` button under the list of analysers. Then click the
`Apply` button at the bottom right of the window. Then click the `Analyze`
button. Note, this process takes ~1 hour for the `main` file of The Legend of
Zelda: Skyward Sword HD.

![The Ghidra "Analysis Options" window with all the analyzers selected. The description and options on the right show information about the `(Switch) IPC Analyzer`.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/analysis-options.png?raw=true)

You can monitor the progress of the analysis in the bottom right corner of the
`CodeBrowser` Ghidra window you opened when double-clicking on your imported
code file.

![The bottom right corner of the Ghidra "CodeBrowser" window showing early progress of the analysis of the main code file from The Legend of Zelda: Skyward Sword HD.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/analysis-progress.png?raw=true)

After the analysis is completed, the progress indicator at the bottom right of
the `CodeBrowser` window should disappear and you should be able to interact
with your code file.

![The Ghidra "CodeBrowser" window after the analysis has completed.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/analysis-completed.png?raw=true)

### Changing the Memory Offset (Set Image Base)

After looking around at the code, you may notice that Ghidra defaults the
starting address of your code file to be `0x7100000000`. This may not be
appropriate for your use-case.

To change this, go to:

`Window -> Memory Map`

![The Ghidra "Window" menu with the "Memory Map" option selected.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/memory-map.png?raw=true)

This will open the `Memory Map` window. To change the starting address that
Ghidra shows, you will need to use the `Set Image Base` option. This option
looks like a small house and on the right side of the window with several
other option buttons. Click the house icon.

![The Ghidra "Memory Map" window with the "Set Image Base" (the small house) icon selected.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/memory-map-set-image-base.png?raw=true)

The `Base Image Address` window will open. Here, replace the number shown with
starting address that you prefer and click `OK`. Note, this address is a
hexadecimal number and your new starting address should also be a hexadecimal
number.

You may be shown an error popup window after the relocation is completed. This
can be ignored in most cases.

![The Ghidra "Base Image Address" window with the textbox value changed to the starting address used for the main code file of The Legend of Zelda: Skyward Sword HD.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/base-image-address.png?raw=true)

### Save the Analysed Code

After analysing your code file, you will want to create a copy of it so it can
be used in the future. When applying the shared Ghidra information (names,
types, function definitions, etc), you need to do this onto a newly analysed
copy of the code file.

It is recommended to create new folder in your Ghidra project to store all of
the freshly analysed code files. To do this, right-click on the root folder of
your Ghidra project and select the `New Folder` option.

![The Ghidra "New Folder" option.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/new-folder.png?raw=true)

Then, click and drag your analysed code file into the newly created folder.
Rename this file to indicate that it is your analysed copy of the code file.

Copy your analysed code file and drag the copy into the root of your Ghidra
project. Rename this file to indicate that this is your working copy of the
code file.

The end result should look something like this:

![The Ghidra "Active Project" section of the main Ghidra window showing an example structure for The Legend of Zelda: Skyward Sword HD Ghidra project. The root folder contains: main, rtld, sdk, subsdk0, subsdk1 files and a folder called "analysed". Within the folder, there are copies of the code files with "-analysed" appended to their names.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/example-project-structure.png?raw=true)

## Importing Shared Documentation

The purpose of this repository is to allow people to share their documentation
of the code files for The Legend of Zelda: Skyward Sword HD. This information
is stored in the `exefs` directory of this repository. Each code file has a
`.xml` file that stores all of the documentation we have accumulated for a
given code file.

### Pre-requisites

The `.xml` files can only be applied to a freshly analysed copy of the
corresponding code file with the correct starting address.

The correct starting addresses for each file are as follows:
* `rtld    -> 0x08000000`
* `main    -> 0x08004000`
* `sdk     -> 0x360a5000`
* `subsdk0 -> 0x35037000`
* `subsdk1 -> 0x359ff000`

You will need to download the `.xml` file for each code file you intend to
interact with from the `exefs` directory of this repository.

### Importing the Documentation

First, open the code file you wish to import the documentation into with the
Ghidra `CodeBrowser` (double-click on the file name). Then, go to:

`File -> Add to Program...`

![The Ghidra "File" menu selected on the "Add to Program" option.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/add-to-program.png?raw=true)

Next, select the appropriate `.xml` file in your file system that you would
like to import. This should open the `Add to Program` window.

The information should be automatically filled for you. The `Language`,
`Destination Folder`, and `Program Name` fields should be filled out in the
same way they were when you initially imported the code file and they should
be greyed-out and uneditable. The `Format` field should already be set to
`XML Input Format` and should not be changed.

When you have confirmed the information is correct, click `OK`.

![The Ghidra "Add to Program" window with the fields filled out appropriately.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/add-to-program-format-and-language.png?raw=true)

Ghidra will then perform an analysis on the file as it imports it into the
code file. You will likely get the following XML error shortly after clicking
`OK`. This is because Ghidra doesn't expect the XML file to contain
information in the `.xml` file header despite giving this extra information in
the file header when exporting as XML. This error can safely be ignored.

![The Ghidra "XML Error" window showing an issue with the XML file header format that can safely be ignored.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/xml-error.png?raw=true)

Once the analysis of the `.xml` file is completed, you can then interact with
the code file and document anything you find. If you wish to contribute to
this repository, please read the following section carefully before submitting
a pull request.

## Contributing

If you have successfully imported the existing documentation for a code file
into your own Ghidra project and have made additional progress in documenting
the code file, you can submit a pull request to this repository to share your
work with others.

However, you must export the code data in a specific way in order to ensure
other people can benefit from your work and that Nintendo's proprietary works
aren't uploaded to this repository.

**
This repository does not contain proprietary Nintendo works and the
contributors to this repository do not endorse the distribution of such works.
**

### Pre-requisites

Due to the size of the `.xml` files produced by Ghidra, you will need to
install `Git Large File Storage (lsf)` in order to contribute to this
repository. To do this, run the following command line command:

`git lfs install`

### Exporting Documentation

First, right-click on the code file you want to export the data from.

`Right-click -> Export...`

![The Ghidra right-click menu with the "Export" option selected.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/export.png?raw=true)

This will open the `Export` window. Click on the `Format` option and ensure it
is set to `XML`. Then, click on the `Options...` button. This will open the
`Options` window for the export. Make sure all options are selected except for
the `Memory Contents` option. **Do not select the `Memory Contents` option!**

When you are sure the options are correct, click on the `OK` button on the
`Options` window. Make sure the `Output File` field has the correct location
that you would like the outputted `.xml` file to be placed and then click the
`OK` button on the `Export` window.

![The Ghidra "Export" window showing the "Format" field set to "XML" as well as the "Options" window with the "Memory Contents" option NOT selected.](https://github.com/mint-choc-chip-skyblade/sshd-ghidra/blob/main/assets/export-format-and-options.png?raw=true)

### Pull Requests

Please follow the provided pull request template when contributing to this
repository. Please give details about what you have changed - this will help
speed up the process of reviewing and merging your changes.
tions.png?raw=true)
