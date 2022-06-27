# 01 Installing A Domain Controller
## Using Windows Server 2022 

1. You can use SConfig if headless or Windows Server Manager if using the GUI - We need to configure the server with the below attributes
        - Change Hostname
        - Change IP to static
        - Change DNS to the servers IP (keep cheching this as ADDS set up loves to change it to loopback address)
        - Create Domain Admin and Domain User accounts for management and connection workstations to the Domain

2. Install ADDS - Active Directory Domain Services - Feature via GUI or if using terminal with the below command

```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

