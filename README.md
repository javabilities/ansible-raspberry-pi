# ansible-raspberry-pi

Ansible playbooks for a Raspberry Pi cluster.

## Roles

### common
The common role installs common packages and sets basic environment settings.
* Installs the build-essentials package.
* Adds aliases and settings to the pi and root user environments.
* Adds cluster hosts to /etc/hosts.

### go1.9
The go1.9 role will install and configure go 1.9.x.
* Go is installed in /usr/local/go.
* The GOROOT environment variable is /usr/local/go.
* The GOPATH environment variable is /home/pi/Development/go and the directory is created.

### hadoop-common
The hadoop-common role installs and configures hadoop components needed by the master and the slave nodes.
* Create the hadoop tmp and hdfs directories in /home/pi/hadoop.
* Download and explode the hadoop tarball in /home/pi/hadoop.
* Adds hadoop and java environment variables to the user .bashrc file.

### hadoop-master-nodes
The hadoop-master-nodes role depends on the hadoop-common role and configures the hadoop components needed by the master nodes.
* Updates the following files:
  * core-site.xml
  * mapred-site.xml
  * hdfs-site.xml
  * hadoop-env.sh
  * masters
  
### hadoop-slave-nodes
The hadoop-slave-nodes role depends on the hadoop-common role and configures the hadoop components needed by the slave nodes.
* Updates the following files:
  * core-site.xml
  * mapred-site.xml
  * hdfs-site.xml
  * hadoop-env.sh
  * masters
  
### mpi
The mpi role will install and configure mpi tools.
* Install gfortran.
* Create the Fortran source directory in /home/pi/Development/fortran.

### update
The update role will update and clean the operating system.
* Upgrade all packages to the latest version.
* Remove dependencies that are no longer required.
