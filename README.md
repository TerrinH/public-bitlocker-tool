<<<<<<< HEAD
# public-bitlocker-tool
A public version of my production-level BitLocker Tool, modified in ways that make it less specific to one environment.

How it Works:

The tool was designed to be run from a flash drive so that the user may modify a BitLocker encryption state of a multitue of Windows OS
devices relatively quickly without using the Windows GUI. The BitLocker tool does this through the MANAGE-BDE command-line. As of now the
tool assumes the drive letter to be encrypted is C: and that the tool is being run from a flash drive (or any removable media). When 
saving BitLocker ID and keys the tool uses the device's serial number as reported from BIOS as the name of the text file in the selected
sub-directory.

Features:

- Automatic Administrative Privillages:
  Automatically runs and requests administrative privillages if the tool doesn't already have them. This is done with a VBS code snippet 
  I obtained from somehwere on the internet (sorry anonymous contributor).

- Enable BitLocker:
  This allows the user to select from a list of valid encryption options based on the Windows OS it is run on. The list is dynamically 
  generated by querying the OS and is in no way static. After selecting an encryption method another dynically generated menu will ask 
  which sub-directory (customer directory) the user wants to save the keys to, or optionally create a new one, and restarts the device 
  to begin encryption.
  
- Disable BitLocker:
  Fairly self-explainatory I think, in addition to removing any BitLocker encryption the tool will ask for the sub-directory the keys 
  were previously saved to and try to delete those keys. This deletion process is meant to quickly resolve incorrect encryptions and 
  as such is not robust enough to look past keys saved within the same day.
    
- Show De/Encryption Progress:
  Displays the current progress of encyprion operations on an infinite loop that can be broken with Ctrl + C.

- Show BitLocker ID and Keys for Local Machine:
  Simply displays the "MANAGE-BDE -STATUS C:" results, additionally it allows the user to save the information to a sub-directory in the
  event it isn't already present for some reason.
