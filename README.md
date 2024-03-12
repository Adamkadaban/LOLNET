# LOLNET
Living off the Land .Net payloads for when powershell modules aren't available

The goal of this repo is to eventually aggregate all of this information into a queryable site like that of [LOLBAS](https://lolbas-project.github.io/). For now, I'm placing everything in this readme.

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

**Get information about the current domain (`Get-ADDomain`)**
```pwsh
[System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain().DomainControllers
```
Attributes:
- Forest
- DomainControllers
- Children
- DomainMode
- Parent
- PdcRoleOwner
- RidRoleOwner
- InfrastructureRoleOwner

**Get information about domain trusts (`Get-ADTrust`)**
```pwsh
([System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()).GetAllTrustRelationships()
```

**Find all discoverable domain controllers**
```pwsh
([System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()).FindAllDiscoverableDomainControllers()
```

## Site 

**Get information about the current site**
```pwsh
 [System.DirectoryServices.ActiveDirectory.ActiveDirectorySite]::GetComputerSite()
```
Attributes:
- Name
- Domains
- Subnets
- Servers
- AdjacentSites
- SiteLinks
- InterSiteTopologyGenerator
- Options
- Location
- BridgeheadServers
- PreferredSmtpBridgeheadServers
- PreferredRpcBridgeheadServers
- IntraSiteReplicationSchedule


## Files

* Get Attributes of a File
```pwsh
[System.IO.File]::GetAttributes("C:\Users\Administrator\Desktop\root.txt")
```

## Environment

* Check if currently in a 64-bit process
```pwsh
[System.Environment]::Is64BitProcess
```
## Identity

* Get the current identity of the user
```pwsh
[System.Security.Principal.WindowsIdentity]::GetCurrent()
```
- Name
- AuthenticationType
- Groups
- User
- Token
- ImpersonationLevel
- Owner
- IsSystem
- IsGuest
- IsAnonymous
- IsAuthenticated
- AccessToken
- UserClaims
- DeviceClaims
- Claims

# Sources

* This is **largely** based on the series [PowerShell: Using Active Directory .Net methods in PowerShell](https://adsecurity.org/?p=113) by Sean Metcalf
