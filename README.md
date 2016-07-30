# bdutil-ambari

> Install prerequisite

```sh
sudo apt-get install git
```

> Install bdutil

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
# Cluster 1 configuration file
./bdutil --project scrib-tech-2 --bucket scrib-tech-4 --default_fs hdfs \
--zone europe-west1-c --num_workers 2 --machine_type n1-standard-1 \
--image ubuntu-14-04 --worker_boot_disk_size_gb 50 --master_boot_disk_size_gb 100 \
--prefix spark-cluster --verbose generate_config --force spark_dev_env.sh

# Cluster 2 configuration file
./bdutil --project scrib-tech-2 --bucket scrib-tech-2 --default_fs hdfs \
--zone europe-west1-c --num_workers 4 --machine_type n1-standard-1 \
--image ubuntu-14-04 --worker_boot_disk_size_gb 50 --master_boot_disk_size_gb 100 \
--prefix ambari-cluster --verbose generate_config --force ambari_env.sh

# Add execution right on ambari_env.sh file
chmod 777 ambari_env.sh

# Print ambari_env.sh file content
cat ambari_env.sh
```

> Deploy ambari cluster

```sh
# Deploy cluster 1
./bdutil --f -e spark_dev_env.sh,extensions/querytools/querytools_env.sh,extensions/spark/spark_env.sh deploy

# Deploy cluster 2
./bdutil -f -e ambari deploy

```

> Delete cluster

```sh
./bdutil -f -e spark_dev_env delete

./bdutil -f -e ambari delete
```
