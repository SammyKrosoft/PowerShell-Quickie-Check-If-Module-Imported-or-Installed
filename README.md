# PowerShell-Quickie-Check-If-Module-Imported-or-Installed

Quick PowerShell instructions sequence to check if a module is imported, installed, and giving indications to check if it's available on the Online Repository (PowerShellGallery)

```powershell
$m = "ExchangeOnlineManagement"

# First, check if your module is loaded aka "imported":
if (Get-Module $m){
    Write-Host "Module is already imported aka loaded on the current PowerShell session" -ForegroundColor Green
} # Second if it's not imported, check if your module is installed, if it's installed, import it
elseif (Get-Module -ListAvailable $m){
    Write-Host "Module ""$m"" is not loaded, checking if it's installed aka on the disk" -ForegroundColor Yellow
    Write-Host "Module ""$m"" is installed on disk but not imported, importing it now..." -ForegroundColor Green
    Import-Module $m
} # Third if we're on the below Else, that means the module is even not installed on the disk - showing how to find and install it
#NOTE: leaving you the choice not executing the Find-Module / Install-Module as it can take time.
Else {
    Write-Host "*** Module ""$m"" is not loaded, and not even installed aka not on the disk. ***" -ForegroundColor red
    Write-Host "Check if module named ""$m"" is available on the Online gallery using " -ForegroundColor Green
    write-Host "PS > Find-Module -Name ""$m""" -ForegroundColor Yellow
    Write-Host "Then Install the module on the disk using the following:" -ForegroundColor Green
    Write-Host "PS > Install-Module -Name ""$m"" -Force -Verbose -Scope CurrentUser" -ForegroundColor Yellow
    write-Host "Then Import the module aka load it on your PowerShell session using:" -ForegroundColor Green
    Write-Host "PS > Import-Module ""$m"""
}
```

The same as the above, in one line (for copy/paste in a text-only PowerShell console):

```powershell
$m = "ExchangeOnlineManagement";if (Get-Module $m){Write-Host "Module is already imported aka loaded on the current PowerShell session" -ForegroundColor Green}elseif (Get-Module -ListAvailable $m){Write-Host "Module ""$m"" is not loaded, checking if it's installed aka on the disk" -ForegroundColor Yellow;Write-Host "Module ""$m"" is installed on disk but not imported, importing it now..." -ForegroundColor Green;Import-Module $m}Else {Write-Host "*** Module ""$m"" is not loaded, and not even installed aka not on the disk. ***" -ForegroundColor red;Write-Host "Check if module named ""$m"" is available on the Online gallery using " -ForegroundColor Green;write-Host "PS > Find-Module -Name ""$m""" -ForegroundColor Yellow;Write-Host "Then Install the module on the disk using the following:" -ForegroundColor Green;Write-Host "PS > Install-Module -Name ""$m"" -Force -Verbose -Scope CurrentUser" -ForegroundColor Yellow;write-Host "Then Import the module aka load it on your PowerShell session using:" -ForegroundColor Green;Write-Host "PS > Import-Module ""$m"""}
```
