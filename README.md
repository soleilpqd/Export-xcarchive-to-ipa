Export-xcarchive-to-ipa
=======================

XCode 6 now requires Apple ID to make IPA file. To make an IPA file with a profile without Apple ID we can use terminal:
```
xcodebuild  -exportWithOriginalSigningIdentity
```
to export xcarchive to IPA using profile used to create the xcarchive.
These workflows are Automator wrapper for that terminal command line to easy use in Finder. They're wrote in AppleScript and shell script.

- **Export to IPA.workflow**: Finder service
- **ExportIPA.workflow**: Finder folder action

####INSTALL####

To install Folder action workflow:
- Copy "ExportIPA.workflow" as:

> ~/Library/Workflows/Applications/Folder Actions/ExportIPA.workflow

- In Finder, right click on target folder, select "Folder Actions Setup...".
- Select "ExportIPA.workflow" to attach in "Folder Actions Setup".

To install Finder Service workflow: 
- Copy "Export to IPA.workflow" as:

> ~/Library/Services/Export to IPA.workflow

####USAGE####

- Setting the profile of project and make archive in XCode.
- In Organizer, right click on target archive and select <code>Show in Finder</code> (we can also book mark <code>~/Library/Developer/Xcode/Archives</code>).

**Folder action:**
- Drag (or copy & paste) xarchvie into target folder.
- Enter the name of IPA (without extension). The IPA file will be created inside the target foler.

**Finder service:**
- Right click on xcarchive, select <code>Export to IPA</code> in popup menu (maybe in submenu <code>Services</code>).
- Enter the name (without extension) and select path to save the IPA file.
 
- Wait for script running (see icon in System menu bar).
- On finish success, Finder will show the IPA file. On fail, output of xcodebuild is wrote into *path of ipa/ipa name*.txt.
