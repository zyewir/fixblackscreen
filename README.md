# How to Reset Refresh Rate in macOS After Setting It Incorrectly (Black Screen Fix)

This guide provides a step-by-step solution for resetting the refresh rate in macOS when setting an unsupported value causes the screen to go black.

## Prerequisites

- Access to macOS recovery mode or a system where System Integrity Protection (SIP) is disabled.
- Basic familiarity with terminal commands.

## Steps to Fix

### 1.Mount the File System in Read/Write Mode
Boot into macOS recovery mode or another accessible terminal, and mount the file system with write permissions:
```bash
mount -uw /Volumes/MacOs
```
### 2.Replace /Volumes/MacOs with the appropriate volume name if your macOS installation resides in a different volume.

### 3.Locate the Problematic Configuration Files
Search for the configuration files related to display settings and WindowServer:
```bash
find /Volumes/MacOs/ -name "com.apple.preference.displays" 2>/dev/null
find /Volumes/MacOs/ -name "com.apple.windowserver.plist" 2>/dev/null
```
### 4.Remove the Corrupted Files
Navigate to the directories where the files are located and delete them using the following commands:
```bash
rm -f com.apple.windowserver.plist
rm -f com.apple.preference.displays
```
### 5.Restart Your System
After removing the files, restart your Mac. The system will regenerate the default configuration files, restoring display settings and resolving the black screen issue.

## Why This Works

When an unsupported refresh rate is set, macOS may fail to display properly. Deleting the corrupted preference files allows the system to revert to default settings, enabling normal screen behavior.

## Warning

Ensure you know what you are doing before removing system files.

Always back up your data to avoid unintended loss.

## License

This guide is provided under the MIT License.

