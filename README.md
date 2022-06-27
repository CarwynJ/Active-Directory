# 01 Installing A Domain Controller
## Using Windows Server 2022 as a DC 

1. You can use SConfig if headless or Windows Server Manager if using the GUI - We need to configure the server with the below attributes
        - Change Hostname
        - Change IP to static
        - Change DNS to the servers IP (keep cheching this as ADDS set up loves to change it to loopback address)
        - Create Domain Admin and Domain User accounts for management and connection workstations to the Domain

2. Install ADDS - Active Directory Domain Services - Feature via GUI or if using terminal with the below command

```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

#  02 Connecting Clients to the Domain
## Using Windows11 as client

1. First off, make sure your DNS settings are correct as without this the client will not be able to resolve the Domain controller and will fail to connect. To set the DNS address via terminal use the below commands


<em>To show the DNS servers of all interfaces</em>
```shell
Get-DnsClientServerAddress
```
<em>To change DNS server for a desired interface</em>

```shell
Set-DnsClientServerAddress -InterfaceIndex 5 -ServerAddresses 192.168.1.179
```

2. To join the client to the domain you will need to use a **domain user account**
```shell
Add-Computer -DomainName test.com -Credential test\ADadmin -Force -Restart
```

