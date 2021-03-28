# ABAP Platform 1909 Developer Edition on SAP SAP HANA 2.0

## Links
- [ABAP Development Tools](https://tools.hana.ondemand.com/#abap)
- [SAP GUI](https://developers.sap.com/trials-downloads.html?search=ABAP+Platform+1909)
- [Blog - SAP ABAP Platform 1909, Developer Edition](https://blogs.sap.com/2021/02/15/sap-abap-platform-1909-developer-edition-available-soon/)
- [ABAP Platform, Developer Edition on Docker Hub](https://hub.docker.com/_/sap-abap-trial)
- [Setup instructions](https://hub.docker.com/_/sap-abap-trial/plans/ac8a4f9b-ae29-4afa-9b39-25aeea24b821?tab=instructions)
- [ABAP Git](http://eclipse.abapgit.org/updatesite/)

## ABAP Environment

### Setup
```sh
> docker login
> docker pull store/saplabs/abaptrial:1909
> sudo sysctl vm.max_map_count=2147483647
> sudo sysctl fs.file-max=20000000
> sudo sysctl fs.aio-max-nr=18446744073709551615
> docker run --stop-timeout 3600 -i --name a4h -h vhcala4hci -p 3200:3200 -p 3300:3300 -p 8443:8443 -p 30213:30213 -p 50000:50000 -p 50001:50001 --sysctl kernel.shmmni=32768 store/saplabs/abaptrial:1909 -agree-to-sap-license
```

### Start
```sh
> sudo sysctl vm.max_map_count=2147483647
> sudo sysctl fs.file-max=20000000
> sudo sysctl fs.aio-max-nr=18446744073709551615
> docker start -ai a4h
```

### Stop
#### From host
```sh
> docker stop --time 7200 a4h
```
#### From container
```sh
> Ctrl-C
```

### Login
Users: SAP*, DEVELOPER, BWDEVELOPER  
Password: Ldtf5432

## SAP Cloud Connector

### Start
```sh
> docker exec -it a4h bash
> /usr/local/sbin/rcscc_daemon start
```

### Stop
```sh
> /usr/local/sbin/rcscc_daemon stop
> exit
```

### Web UI
https://localhost:8443/  
User: Administrator  
Password: manage

### Connect to SAP BTP
https://developers.sap.com/tutorials/cp-launchpad-federation-connectivity.html  
https://blogs.sap.com/2018/11/12/how-to-setup-cloud-connection/

## Use ABAP Git in ADT (Eclipse)
### Backend
- Transaction: ZABAPGIT
- Pull from https://github.com/abapGit/abapGit (might have to switch branch from master to main)
- Clone from https://github.com/abapGit/ADT_Backend
### ADT
Software Sites
- [Lightweight Eclipse installation](https://blogs.sap.com/2021/03/19/lightweight-eclipse-installation-or-yet-anther-blog-post-about-installing-eclipse/)
- https://tools.hana.ondemand.com/latest
- https://eclipse.abapgit.org/updatesite