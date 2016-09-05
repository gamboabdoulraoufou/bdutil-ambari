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

> Create configuration file

```sh
# Edit ambadi conf file and set your deployment configuration
nano platforms/hdp/ambari.conf

# Add execution right on ambari_env.sh file
chmod 777 ambari_env.sh

# Print ambari_env.sh file content
nano ambari_env.sh
```

> Deploy ambari cluster

```sh
# Deploy cluster
./bdutil -f -e ambari deploy

```

> Delete cluster

```sh
./bdutil -f -e ambari delete
```
