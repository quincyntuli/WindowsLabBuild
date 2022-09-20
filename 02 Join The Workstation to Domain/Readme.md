## Join the workstation to the Domain

Now that the server is setup it is time to joing the workstation to the domain. However the workstation needs to point its dns resolver settings to the new server. After that is done, the computer will be able to join the domain.

### Changing the DNS server of the workstation

#### Discovering the InterfaceIndex of computer

> - Discover current IP Address
> - Discover IntterfaceIndex associated with that IP
> - Construct Powershell command to set DNS Addresses for that Interface


```cmd
ipconfig 
```

![ipconfig](images/ipconfig-01.png)

```powershell
Get-NetIPAddress -IPAddress 192.168.1.15
```

![Find out the Interface Index](images/InterfaceIndex.png)

Construction the powershell command ...

```powershell
Set-DnsClientServerAddress -InterfaceIndex 4 -ServerAddresses ("192.168.1.155","192.168.1.254")
```

Execution ...

![command sequence](images/execution.gif)