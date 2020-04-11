# Google Cloud Learning
## Setup
### Guide
#### Install
https://cloud.google.com/sdk/docs/quickstart-macos

```console
$ wget https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-288.0.0-darwin-x86_64.tar.gz

$ gunzip google-cloud-sdk-288.0.0-darwin-x86_64.tar.gz

$ tar -xvf google-cloud-sdk-288.0.0-darwin-x86_64.tar

$ ./google-cloud-sdk/install.sh

$ gcloud init

```

Example Output

```
Your current project has been set to: [acelearning-273910].

Not setting default zone/region (this feature makes it easier to use
[gcloud compute] by setting an appropriate default value for the
--zone and --region flag).
See https://cloud.google.com/compute/docs/gcloud-compute section on how to set
default compute region and zone manually. If you would like [gcloud init] to be
able to do this for you the next time you run it, make sure the
Compute Engine API is enabled for your project on the
https://console.developers.google.com/apis page.

Created a default .boto configuration file at [/Users/subratamazumder/.boto]. See this file and
[https://cloud.google.com/storage/docs/gsutil/commands/config] for more
information about configuring Google Cloud Storage.
Your Google Cloud SDK is configured and ready to use!

* Commands that require authentication will use subrata.besu@gmail.com by default
* Commands will reference project `acelearning-273910` by default
Run `gcloud help config` to learn how to change individual settings

This gcloud configuration is called [default]. You can create additional configurations if you work with multiple accounts and/or projects.
Run `gcloud topic configurations` to learn more.

Some things to try next:

* Run `gcloud --help` to see the Cloud Platform services you can interact with. And run `gcloud help COMMAND` to get help on any gcloud command.
* Run `gcloud topic --help` to learn about advanced features of the SDK like arg files and output formatting

```
#### Verify Setup

```console
$ gcloud info
```

## Reference
For AWS experts https://cloud.google.com/docs/compare/aws






