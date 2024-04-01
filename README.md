## About the Project
<img src="./imgs/SQL%20Server%20Management%20Studio.png" alt="SSMS" width="600" />


## Built With
Core technologies used in this project

* ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
* ![MicrosoftSQLServer](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft%20sql%20server&logoColor=white)
* ![Microsoft Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

<br />

# Getting Started 

## SQL Management Studio and Database Restore Set-Up

### 1. Download .bak file and Create a new container
First, we'll set up a container using a Docker image. This container will run the preview version of Microsoft SQL Server 2022 on Ubuntu 22.04. To do this, just run this command:

```docker
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=CSA103-StrongPassword" -e
"MSSQL_PID=Evaluation" -p 1433:1433 --name CSA103 --hostname CSA103 -d
mcr.microsoft.com/mssql/server:2022-preview-ubuntu-22.04
```
>Note that the password is **CSA103-StrongPassword** and the Port is **1433**

>After you execute the previous command, your container key (similar to this one: 3dc01d8030005a92ee8f88bc3f00e65f847e73756f3347d898eb571b0f281c3d) will be returned on your CLI. Make sure to store it somewhere accessible for later use.

Next, download the .bak file. You can find the **AdventureWorks2022.bak** file on this [link](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms).

Once the download is complete, navigate to the folder where the **AdventureWorks2022.bak** file is located and run the following command (this will copy the .bak file into your container):

```docker
docker cp AdventureWorks2022.bak your_container_key_here:/var/opt/mssql/data
```
>Make sure you replace "your_container_key_here" with your container key that you saved in part 1

### 2. Start container
Once you execute the previous command, a new container will appear in your Docker Desktop app. If the container is not already running, you can start it by clicking on the "Start" button (See the image bellow)

<img src="./imgs/docker.png" alt="Docker Desktop App" width="600" />

### 3. Connect to the server using Microsoft SQL Server Management Studio
Now that your container is up and running, use Microsoft SSMS to connect to your local SQL Server.

<img src="./imgs/SSMS.png" alt="SQL Server Managament Studio Interface" width="600" >

<blockquote>

Server Name: **,.1433** 

Login: **sa** 

Password: **CSA103-StrongPassword**
</blockquote>

### 4. Restore Adventure Works Database
Now, we need to restore the Adventure Works Database using a BACPAK file.

<img src="./imgs/restore.png" alt="SSMS Object Explorer" height="400" /> <img src="./imgs/device.png" height="400" /> <img src="./imgs/add.png" height="400"> <img src="./imgs/file.png" height="400" />

## :warning: Attention. You need to check this box to be able to restore the database successfully.

<img src="./imgs/checkbox.png" width="600"/>