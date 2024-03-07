# Helpful-CMD-Commands
This will just be a bunch of CMD commands that I use often, but sometimes forget, so I want to make sure I have a place to reference them.

# Scan for DCU updates
"C:\Program Files\Dell\CommandUpdate\dcu-cli.exe" /scan
"C:\Program Files (x86)\Dell\CommandUpdate\dcu-cli.exe" /scan

# Scan for BIOS DCU updates
"C:\Program Files\Dell\CommandUpdate\dcu-cli.exe" /scan -updateType=bios
"C:\Program Files (x86)\Dell\CommandUpdate\dcu-cli.exe" /scan -updateType=bios

# Auto-Suspend Bitlocker for DCU
"C:\Program Files\Dell\CommandUpdate\dcu-cli.exe" /configure -autoSuspendBitLocker=enable -silent
"C:\Program Files (x86)\Dell\CommandUpdate\dcu-cli.exe" /configure -autoSuspendBitLocker=enable -silent

# Apply all DCU updates (no reboot)
"C:\Program Files\Dell\CommandUpdate\dcu-cli.exe" /applyUpdates -reboot=disable
"C:\Program Files (x86)\Dell\CommandUpdate\dcu-cli.exe" /applyUpdates -reboot=disable

# Apply BIOS DCU updates ONLY (no reboot)
"C:\Program Files\Dell\CommandUpdate\dcu-cli.exe" /applyUpdates -updateType=bios -reboot=disable
"C:\Program Files (x86)\Dell\CommandUpdate\dcu-cli.exe" /applyUpdates -updateType=bios -reboot=disable

# Endpoint Central Agent apply updates
"C:\Program Files (x86)\DesktopCentral_Agent\bin\cfgUpdate.exe"
"C:\Program Files (x86)\ManageEngine\UEMS_Agent\bin\cfgUpdate.exe"

# Powershell Connect Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName navin@contoso.com

# Disable IPv6
powershell -command "Disable-NetAdapterBinding -Name 'Wi-F*' -ComponentID ms_tcpip6"
powershell -command "Disable-NetAdapterBinding -Name 'Etherne*' -ComponentID ms_tcpip6"

# Server
sconfig

# Remove Mac user as admin user
sudo dseditgroup -o edit -d UserName -t user admin

# Scan for hardware changes
timeout 15 & pnputil.exe /scan-devices

# Fixes corrupted group policy issues
cd C:\Windows\System32\GroupPolicy
for /r %x in (registry.pol) do ren "%x" registry.pol.bak
gpupdate /force

# Re-Connect FortiEMS after disconnection
C:\"Program Files"\Fortinet\FortiClient\FortiESNAC.exe -r ems.yourdomain.com

# DCU one-liner with forced restart
"C:\Program Files\Dell\CommandUpdate\dcu-cli.exe" /applyUpdates -reboot=enable & "C:\Program Files (x86)\Dell\CommandUpdate\dcu-cli.exe" /applyUpdates -reboot=enable & shutdown /r -t 600

# Schedule Shutdown (kinda)
C:\system32\shutdown.exe /r /t ([decimal]::round(((Get-Date).Date.AddHours(11).AddMinutes(45) - (Get-Date)).TotalSeconds)) /c " "

# Export User AD Groups
Get-ADPrincipalGroupMembership <USERNAME> | Select name | Export-Csv C:\Users\larsen.orchard\Downloads\<USERNAME>Groups.csv
(Get-ADPrincipalGroupMembership <USERNAME>).name

# Send to Bitlocker Recovery
powershell -command "manage-bde -forcerecovery C:" & shutdown /s
![image](https://github.com/orchardl/Helpful-CMD-Commands/assets/98601653/76cc836b-1664-4e09-8773-b05d3f0f3ec6)

