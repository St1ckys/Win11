If you don’t mind doing some registry adjustments in order to avoid using WinPass11 Guided Installer as presented above, you can also opt to build the Secure Boot and TPM 2.0 bypassing mechanisms yourself via Registry Editor.

If TPM 2.0 is not supported on your hardware and your CPU is not able to virtualize the technology via PTT or fTPM, you should be able to bypass the compatibility check by making the following changes:

Press Windows key + R to open up a Run dialog box. Next, type ‘regedit’ inside the text box and press Ctrl + Shift + Enter to open an elevated Registry Editor window.

Opening Regedit
Note: When you see the UAC (User Account Control), click Yes to grant admin access.

Once you’re inside the Registry Editor, navigate to the following location using the left-hand side menu:
HKEY_LOCAL_MACHINE\SYSTEM\Setup
Once you arrive at the correct location, right-click on Setup and choose New > Key.

Creating a new Key
Name the newly created key LabConfig and press Enter.
Next, right-click on the newly created LabConfig key and choose New > Dword (32-bit) Value.

Creating a new Dword key
Name the newly created key BypassTPMCheck.
Next, double-click on it and set the base to Hexadecimal and the Value to 1.
Note: By enforcing this value, you have successfully disabled TPM Check.
Now to disable Secure Boot check, right-click on LabConfig once again and choose New > Dword (32-Bit) Value.
PRO TIP: If the issue is with your computer or a laptop/notebook you should try using Restoro Repair which can scan the repositories and replace corrupt and missing files. This works in most cases, where the issue is originated due to a system corruption. You can download Restoro by Clicking Here


Creating a new Dword key
Name the newly created DWord value to BypassSecureBootCheck and set its base to Hexadecimal and its Value to 1.
To disable the RAM check, right-click on the LabConfig key once again and select New > Dword (32-bit) Value.
Next, name the newly created value as BypassRAMCheck and set its base to Hexadecimal and it’s value to 1.

Bypassing the RAM check for Windows 11
To disable the CPU check you can simply head over to this new location:-
HKLM\SYSTEM\Setup\MoSetup
Next, create a new DWord value and name it “AllowUpgradesWithUnsupportedTPMOrCPU“ Set it’s value to 1.
Once you get to this point, every potential check that might stop the installation of Windows 11 in its tracks is bypassed. All you need to do is close the Registry Editor, and restart your PC to allow the changes to take effect before retrying the installation.