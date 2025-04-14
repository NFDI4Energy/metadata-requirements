# Requirements Template
This is a repository template to manage the requirements analysis. 
For information regarding the Configuration of this repository please look through the [CONFIGURATION.md](CONFIGURATION.MD).

In this file a README Template will follow:

# NFDI4Energy [TODO_Type] Requirement Collection

This repository serves as the general collection point for NFDI4Energy [TODO_Type] requirements.
The collection was set up as part of the [NFDI4Energy Consortia](https://nfdi4energy.uol.de/).

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#content-of-this-repository">Content of this Repository</a>
      <ul>
        <li><a href="#how-to-look-at-the-requirements">How to look at the Requirements</a></li>
      </ul>
    </li>
    <li>
      <a href="#how-to-contribute">How to contribute</a>
      <ul>
        <li><a href="#contribute-through-an-issue">Contribute through an Issue</a></li>
        <li><a href="#contribute-through-a-pull-request">Contribute through a Pull Request</a></li>
        <li><a href="#contribute-through-mail">Contribute through a Mail</a></li>
      </ul>
    </li>
    <li><a href="#the-metadata-schema">The Metadata Schema</a></li>
    <li><a href="#other-nfdi4energy-requirements">Other NFDI4Energy Requirements</a></li>
  </ol>
</details>

## Content of this Repository

The requirements are listed in a single *.csv* file inside this repository. 
Two other important files are this README.md file, containing the information you are reading right now,
as well as the [Metadata Schema.md](./docs/content/requirements_metadata_schema.md) file, that lists the Metadata Schema we use.

The rest of the files in this repository are used to create a Website that can be used to look at the Requirements.

### How to look at the Requirements

To look through the requirements there are two options.
You can go to this [website](TODO LINK). The site was built using [GitHub Pages](https://pages.github.com/). It should look like this:


![Screenshot of the Requirements Website with example test data](TODO/path/to/img.png "Screenshot of the Website with Example Data")

On this website you can see a interactive table, this table can be sorted according to the different columns and also searched throuh the search bar.

Another way to look through the requirements is by downloading the .csv file and opening it locally on your computer.
The file can be opened by any current spreadsheet software such as [Libre Office Calc](https://de.libreoffice.org/discover/calc/) or [Microsoft Excel](https://www.microsoft.com/de-de/microsoft-365/excel?market=de).

You can download it, by clicking on the requirement folder in the repository and then the requirements.csv file in the repository, then start the download by clicking the download button.

## How to contribute

>[!IMPORTANT]
>Anybody that has Requirements is encouraged to contribute to this collection, regardless if they are affiliated with NFDI4Energy or not.

To add Requirements to this collection there are three possible ways, which will be explained in the following sections. The only method not requiring a Github account is found in <a href="#contribute-through-an-email">Contribute through an E-Mail</a>.

The Reqirments must follow the [Meadata Schema](#the-metadata-schema), there are optional fields and required fields, a requirement will not be accepted if all required fields are not filled in.

### Contribute through an Issue

>[!NOTE]
>A GitHub Account is needed for this Contribution Method.

This is the preffered method for adding a requirement into the collection and recommended for people not familiar with using git or csv files.
This method consists of an issue being opened that contains the relevant requirement information. We have devised a special issue template, that will make adding the requirement easier.
To add an issue simple go to Issues->New Issue on the repository github page.

### Contribute through a Pull Request

>[!NOTE]
>A GitHub Account is needed for this Contribution Method.

This is a secondary method for adding requirements, it is for users that are familiar with using git.
It consists of the following steps:

1. Creating a normal Issue [Todo add issue template]
2. Cloning the repository
3. Creating a branch from the main branch
4. Adding the new requirements into the csv with the tool of your choice
5. Pushing the changes
6. Submitting a [Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)

### Contribute through Mail
>[!NOTE]
>No GitHub Account is needed for this Contribution Method.

If you do not want to use GitHub, you can still submit a requirement via E-Mail.
Please get in touch with us through the following Mail:
[TODO Add E-Mail]

## The Metadata Schema

The Metadata Schema can be found in the [Metadata Schema.md](./docs/content/requirements_metadata_schema.md).
The different fields are also explained in the Markdown file.

>[!WARNING]
>Keep in mind, that some of the fields are optional, whil other are not. A requirement is only accepted when all required fields are filled in.

## Other NFDI4Energy Requirements

Here is a list of NFDI4Energy Requirements repositories:

- [NFDI4Energy Requirements Repository Template](https://github.com/NFDI4Energy/requirements_template)
- [NFDI4Energy Service Requirements](https://github.com/NFDI4Energy/nfdi4energy-service-requirements)
- [NFDI4Energy Simulation Service Requirements](https://github.com/NFDI4Energy/simulation-service-requirements)
- [NFDI4Energy Metadata Requirements](https://github.com/NFDI4Energy/metadata-requirements)
- TODO: Create Issue in Repository Template to add you repository
