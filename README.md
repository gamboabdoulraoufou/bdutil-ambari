# bdutil-ambari

> Install prerequisite

```sh
sudo apt-get install git
```

> Install gcloud sdk

```sh
# Update package source
sudo apt-get update

# Install gcloud
curl https://sdk.cloud.google.com | bash

# authenticate to Google cloud
gcloud auth login                   

```

> Download bdutil

```sh
git clone https://github.com/GoogleCloudPlatform/bdutil 
cd bdutil
```

> Edit and modify the configuration file

```sh
# Edit ambari configuration file and set your deployment configuration
nano platforms/hdp/ambari.conf

```
> Example
![ambari.conf head](https://github.com/gamboabdoulraoufou/bdutil-ambari/blob/master/ambari.conf.png)



> Deploy ambari cluster

```sh
# Deploy cluster
./bdutil -f -e ambari deploy

```

> Go to your google cloud console, you should see your cluster VM

![ambari.conf head](https://github.com/gamboabdoulraoufou/bdutil-ambari/blob/master/console_gcp.png)


> Delete cluster

```sh
./bdutil -f -e ambari delete
```
