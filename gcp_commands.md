# Summary
A list of Google Cloud Platform (GCP) shell commands with examples

## Setup up a Cloud Shell Enivronment
Every time you close Cloud Shell and reopen it, a new VM is allocated. You can create a file to set the value so that you won't have to enter the command each time Cloud Shell is cycled. This can be stored in the Cloud Shell environment as you have 5 GB of persistent disk storage ($HOME dir).

### Create a persistent state in Cloud Shell
1. List the available regions

`gcloud compute regions list`

2. Create an environment variable and replace [YOUR_REGION] with your choice of region.

`INFRACLASS_REGION=[YOUR_REGION]`

3. Verify the environment variable

`echo $INFRACLASS_REGION`

4. Create a subdirectory to store the environment variable

`mkdir infraclass`

5. Create a file called `config` in `infraclass` directory

`touch infraclass/config`

6. Append the value of your Region environment variable to the `config` file

`echo INFRACLASS_REGION=$INFRACLASS_REGION >> ~/infraclass/config`

7. Create an environment variable for your Project ID, replacing `[YOUR_PROJECT_ID]` with your Project ID. You can find the project ID on the GCP Console Home page.

`INFRACLASS_PROJECT_ID=[YOUR_PROJECT_ID]`

8. Append the value of your Project ID environment variable to the `config` file

`echo INFRACLASS_PROJECT_ID=$INFRACLASS_PROJECT_ID >> ~/infraclass/config`

9. Use the source command to set the environment variables, and use the echo command to verify that the project variable was set

```
source infraclass/config
echo $INFRACLASS_PROJECT_ID
```

## `gcloud` working with Compute Engine and GCP services
    gcloud compute instances create [INSTANCE_NAME] // Create a VM
    gcloud compute regions list // List available regions
    gcloud compute instance move // Move an instance to a new zone (w/in same region)
    gcloud compute addresses list // View static IP addresses
    gcloud compute addresses create --region [REGION] [VPN_NAME]-static-ip // Reserve a static IP for VPN gateway 
    // e.g. `gcloud compute addresses create --region US-east1 vpn-1-static-ip`
    gcloud compute target-vpn-gateways create [VPN_NAME] --network [VPN_NETWORK_NAME] --region [REGION]
    // Set up VPN e.g. `gcloud compute target-vpn-gateways create vpn-1 --network vpn-network-1 --region us-east1`
    gcloud config list // List configurations for the current project
    gcloud config list project // List the project ID
    gcloud config list | grep project // List the current project id
    gcloud config set project [PROJECT_ID] // Switch to a different project

## `gsutil` working with Cloud storage
    gsutil mb gs://[BUCKET_NAME] // Create a bucket e.g. `gsutil mb gs://my_bucket`
    gsutil ls gs://[BUCKET_NAME] // View contents of a bucket e.g. `gsutil ls gs://my_bucket`
    gsutil cp [MY_FILE] gs://[BUCKET_NAME] // Copy file from Cloud Shell VM to a bucket
    gsutil cp ‘my file.txt' gs://[BUCKET_NAME] // If filename has whitespaces, ensure to place single quotes around the filename

## `kubectl` working with Container Engine and Kubernetes

## `bq` working with BigQuery

## Info about VM
    free // see information about unused and used memory and swap space on VM
    sudo dmidecode -t 17  // see details about the RAM installed on VM
    nproc // verify the number of processors
    lscpu // see details about the CPUs installed on VM

## Misc
    export <VARIABLE_NAME>=<PROJECT_ID>  // Assign Project ID to a variable e.g. export MY_PROJECT=my_project_123456
    gcloud config set project <VARIABLE_NAME> // To use the new variable, e.g. gcloud config set project $MY_PROJECT
    sudo shutdown -h now // Boot disk, halt the system
    sudo unmount <MOUNT/POINT> // Additional disks, unmount the file system
    sudo sync // Complete pending writes and flush casch. Use if unmount not possible
    sudo fsfreeze -f </MOUNT/POINT> // Suspend writes to disk device
