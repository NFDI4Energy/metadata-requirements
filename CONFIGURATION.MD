This file contains information on how to Configure this template repository. It goes over basic configurations to get this repository running for your use case. For deeper configuration, sch as multiple requirements.csv files, dsiplaying the requirements as Markdown and more a deeper change is needed and thus it will not be covered here.

## Configuration

To configure this Requirement there are 3 files to be changed:

- The README.md
- The index.md
- The mkdocs.yml

Both Markdown Files (.md) have the parts that need to be changed marked with a TODO in the text.
In the mkdocs.yml the following configurations have to be changed:

- site_name
- site_url
- favicon (here images need to uploaded to the docs/img folder)
- logo (here images need to uploaded to the docs/img folder)
- repo_url

## Pulling changes from the template

If the template receives an update, you might want to use the updates within your repository.
The simplest way to do this are the following steps
```
git remote add template git@github.com:NFDI4Energy/requirements_template.git
git fetch --all
git merge template/main --allow-unrelated-histories
```

This way you can merge in the updates from the template repo.
