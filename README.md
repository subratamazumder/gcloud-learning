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
#### Create a new VM with Apache server
```console
$ gcloud compute --project=acelearning-273910 instances create instance-2 --zone=us-west1-b --machine-type=g1-small --subnet=default --network-tier=PREMIUM --metadata=startup-script=\#\!\ /bin/bash$'\n'apt-get\ update$'\n'apt-get\ install\ -y\ apache2$'\n'cat\ \<\<EOF\ \>\ /var/www/html/index.html$'\n'\<html\>\<body\>\<h1\>Hello\ World\</h1\>$'\n'\<p\>This\ page\ was\ created\ from\ a\ simple\ startup\ script\!\</p\>$'\n'\</body\>\</html\> --maintenance-policy=MIGRATE --service-account=805266248939-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --tags=http-server --image=ubuntu-1604-xenial-v20200407 --image-project=ubuntu-os-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=instance-2 --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --labels=name=test --reservation-affinity=any

(optional if already created before)

$ gcloud compute --project=acelearning-273910 firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server
```
Sample output
```
WARNING: You have selected a disk size of under [200GB]. This may result in poor I/O performance. For more information, see: https://developers.google.com/compute/docs/disks#performance.
Created [https://www.googleapis.com/compute/v1/projects/acelearning-273910/zones/us-west1-b/instances/instance-2].
NAME        ZONE        MACHINE_TYPE  PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP   STATUS
instance-2  us-west1-b  g1-small                   10.138.0.3   34.82.54.122  RUNNING
```
#### Verify VM
```console
$ gcloud compute instances list --zones=us-west1-b
```


Open browser and type EXTERNAL_IP's value; A hello world html page should be served by apache server

#### Stop VM
```console
$ gcloud compute instances stop instance-2 --zone=us-west1-b --async
```

## Reference
For AWS experts https://cloud.google.com/docs/compare/aws






