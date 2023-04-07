# aws-undocumented-api-models
Model files for undocumented AWS APIs

# Usage
After checking out this repo, run `git submodule update` to download the repositories linked in the vendor folder.

Include the models directory in the `AWS_DATA_PATH` ([see the botocore documentation][botocore-loaders]).

After that you will have mulitple services starting with an underscore. All availble services are shown by `aws help`

```shell
export AWS_DATA_PATH="${pwd}/models"
aws help
```

# Vendor folder
Some files are already available in other open source projects. We used git submodules and softlinks to include them. These files might come with their own separate license.

# FAQ
## Why are these json files and not smithy models?

Smithy models would be easier to write and maintain, but there is currently no public plugin to convert those models into files the AWS CLI would understand. Since these will be probably used for exploration, cli access is one of the main reasons to have these files.

## Why is there a date of 1970-01-01
Since these are unreleased APIs, most of them don't have versioning that is easy to discover.

## Why are the services called _service?
We don't want have conuision between documented and undocumented AP{Is (some models will have are extra actions on an existing API, some of them might be a service that currently is console only, but will get API access at some point).

In python a single underscore is usually used as a  "weak “internal use” indicator".

## These files are incomplete?
That's not really a question. The model files are (usually) created by looking at the requests the console does. Since this is a timeconsuming process, typically only the actions needed at the time of creation are added.

[botocore-loaders]: https://botocore.amazonaws.com/v1/documentation/api/latest/reference/loaders.html