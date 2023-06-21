# Munki Conditional Items

Offcial Munki documentation about custom conditions : https://github.com/munki/munki/wiki/Conditional-Items#admin-provided-conditions

## Usage - client side
You have to put theses files (not folders !) in __/usr/local/munki/conditions__ (create the conditions folder if is not there) on the Munki client.<br/>
After a standard Munki check, you can look for the 'Conditions' dictionary in /Library/Managed Installs/ManagedInstallReport.plist

## Examples - manifest side

### With the `ws1_smartgroup` script
You can add this code in the site_default manifest to deploy a special manifest for a specific WS1 UEM group only.

```
<key>conditional_items</key>
	<array>
		<dict>
			<key>condition</key>
			<string>ws1_devicesmartgroup CONTAINS "Some WS1 UEM group name"</string>
			<key>included_manifests</key>
			<array>
				<string>some special manifest</string>
			</array>
		</dict>
	</array>
```
	
### For the `test_file`script
You can add this code in any manifest to deploy two special packages only on client where "anyfile" exist.
	
```
<key>conditional_items</key>
	<array>
		<dict>
			<key>condition</key>
			<string>anyfile == 'true'</string>
			<key>managed_installs</key>
			<array>
				<string>special install 1</string>
				<string>special install 2</string>
			</array>
		</dict>
```