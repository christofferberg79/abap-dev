# SAP NetWeaver AS ABAP Developer Edition 7.52 SP04

## Prerequisites
- Docker
- Git
- S-User
- SAP GUI
- Eclipse with ABAP Development Tools (optional)

## SAP NetWeaver AS ABAP

For more detailed instructions: https://github.com/nzamani/sap-nw-abap-trial-docker

1. Download [SAP NetWeaver AS ABAP Developer Edition 7.52 SP04 from SAP](https://developers.sap.com/trials-downloads.html?search=7.52+SP04) to `~/Downloads`

1. Build Docker image
    ```sh
    > git clone https://github.com/nzamani/sap-nw-abap-trial-docker.git
    > cd sap-nw-abap-trial-docker
    > mkdir sapdownloads
    > unrar x ~/Downloads/TD752SP04part01.rar ./sapdownloads
    > docker build -t nwabap:7.52 .
    ```

1. Create the Docker container and install SAP NetWeaver AS ABAP
    ```sh
    > sudo sysctl -w vm.max_map_count=1000000
    > docker run -p 8000:8000 -p 44300:44300 -p 3300:3300 -p 3200:3200 -h vhcalnplci --name nwabap752 -it nwabap:7.52 /bin/bash
    > /usr/sbin/uuidd
    > ./install.sh
        Do you agree to the above license terms? yes/no:
        yes
        Please enter a password:
        Down1oad
        Please re-enter password for verification:
        Down1oad
    > su npladm
    > stopsap
    > exit
    > exit
    ```

1. Starting the container and SAP NetWeaver AS ABAP
    ```sh
    > docker start -i nwabap752
    > /usr/sbin/uuidd
    > su npladm
    > startsap ALL
    ```
1. Stopping SAP NetWeaver AS ABAP and the container
    ```sh
    > su npladm
    > stopsap
    > exit
    > exit
    ```

## Cloud Connector
https://github.com/nzamani/sap-cloud-connector-docker

## SAP Cloud Trial Account
- https://account.hanatrial.ondemand.com/cockpit/ > Enter Your Trial Account
- [Find Your Subaccount ID](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/b43eff2df3f84124995f6acbc9e5c55b.html)