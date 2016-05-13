Ansible In Windows
===============
Setup Ansible For Windows
--------------------
Ansible is a very powerful configuration tools in Unix/Linux.It is also works in windows envionment 
using Microsoft's Powershell 3.0.

Configuring Ansible in Windows is a bit of tricks . We some steps to configure ansible in winndows.
There are some helping library  .ps1  available but you need to understand  that wat is applicable.

Configuring winrm and psremoting:

Powershell comes in built with windows but not activated. Add powershell from features (in case of Server 2008 R2,2012).If the powershell version is not 3.0 update it to 3.0.
    
```Enable-PSRemoting -f```
    
You need a local administartor user (in domain environment) to connect windows node from controller (Linux) Node.
Change the execution policy to remote signed .First check by applying 

```Get-ExecutionPolicy -Scope CurrentUser```
    
if result is Undefined Then  

```Set-ExecutionPolicy -Scope CurrentUser RemoteSigned```
    
Add an exception in firewall.
    
```netsh advfirewall firewall add rule Profile=Domain name="Allow WinRM HTTPS" dir=in localport=5986 protocol=TCPaction=allow```
 
Profile=Domain   for domain level
Profile=Any      for all.
