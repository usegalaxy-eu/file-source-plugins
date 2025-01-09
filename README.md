# file-source-plugins

A resource of pluggable Galaxy file source plugins.

The file [file_sources_conf.yml](./file_sources_conf.yml) can be used to integrate file sources for all users by default.
The files in the [templates](./templates) folder can be used to populate a `config/file_source_templates.yml` file.
In that case, the file source plugins are not activated by default for each user, but they can be activated in each user-preferences.

Many of the resources are provided via S3 by the [Registry of Open Data on AWS](https://registry.opendata.aws/).

## How to add new plugin

1. Add your plugin to [file_sources_conf.yml](./file_sources_conf.yml). You can take inspiration from the [upstream example file](https://github.com/galaxyproject/galaxy/blob/dev/lib/galaxy/config/sample/file_sources_conf.yml.sample). Please only add public resources for now. Resources that can be used by everyone and are free to use without any restrictions.
2. Add a separate file into [templates](./templates). Please prefix the filename with the `protocol` used, e.g. `s3` or `ftp`, followed by the unique ID you are planning to use. For example the bucket name `copernicus-dem-30m`. Use `_` instead of `-`.
