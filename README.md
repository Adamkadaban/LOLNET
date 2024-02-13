# LOLNET
Living off the Land .Net payloads for when powershell modules aren't available


## Forest

**Get information about the current forest (`Get-ADForest`)**
```pwsh
[System.DirectoryServices.ActiveDirectory.Forest]::GetCurrentForest()
```
Attributes:
- Name
- Sites
- Domains
- GlobalCatalogs
- ApplicationPartitions
- ForestMode
- RootDomain
- Schema
- SchemaRoleOwner
- NamingRoleOwner
	

## Domain

* Get information about the current domain (`Get-ADDomain`)
```pwsh
[System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain().DomainControllers
```


## Files

* Get Attributes of a File
```pwsh
[System.IO.File]::GetAttributes("C:\Users\Administrator\Desktop\root.txt")
```


# Sources

* This is **largely** based on the series [PowerShell: Using Active Directory .Net methods in PowerShell](https://adsecurity.org/?p=113) by Sean Metcalf