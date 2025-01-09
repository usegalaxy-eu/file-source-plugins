# file-source-plugins

A resource of pluggable Galaxy file source plugins.

Galaxy `file-sources` are a super easy way to add data repositories to Galaxy. Thanks to @jmchilton for the initial implementation!
There are two ways they can be used in Galaxy.

First, an Admin can configure `file-sources` for all users and can restrict write access to groups/roles etc. Those file sources are usually exposed to all users of the server. We think this is a great way to give users access to 
Zenodo or similar cross-domain data providers. However, if you have community-specific data providers it might be overwhelming for users not from this domain. This is where option 2 comes into play.
We can offer all users a list of public file sources in their user preferences.
Every user can now opt-in to specific repositories before they are displayed in the upload form of Galaxy. The disadvantage is that they are initially hidden in the user-preferences and may not be that visible to the user.

The file [file_sources_conf.yml](./file_sources_conf.yml) can be used to integrate file sources for all users by default, the first option from above.
The files in the [templates](./templates) folder can be used to populate a `config/file_source_templates.yml` file.
In that case, the file source plugins are __not__ activated by default for each user, but they can be activated in each user preference, option two.

In both scenarios, an Admin needs to know about those cool data repositories, either to activate them by default or offer a template in the user-preference. This repo is to collect public, open repositories to make Admin life easier.

Many of the resources are provided via S3 by the [Registry of Open Data on AWS](https://registry.opendata.aws/).

## How to add a new plugin

1. Add your plugin to [file_sources_conf.yml](./file_sources_conf.yml). You can take inspiration from the [upstream example file](https://github.com/galaxyproject/galaxy/blob/dev/lib/galaxy/config/sample/file_sources_conf.yml.sample). Please only add public resources for now. Resources that can be used by everyone and are free to use without any restrictions.
2. Add a separate file into [templates](./templates). Please prefix the filename with the `protocol` used, e.g. `s3` or `ftp`, followed by the unique ID you are planning to use. For example the bucket name `copernicus-dem-30m`. Use `_` instead of `-`.
