# Hybrid Backup Sync Decipher
Currently there is no official tool to decipher files from Hybrid Backup Sync (on QNAP devices) on all plateform.
I've made this tool with some ideas : light (<1MB), fast (<3s for 300MB on my computer), universal, open source, with as less as possible dependencies.

This software is provided without any garanties, use it at your own risk.


# License:

Tool under GNU version 3 license.

# Description:

First of all, this program is not supported or affiliated with QNAP Systems Inc.
It is a small tool to decipher files ciphered with Hybrid Backup Sync with cloud providers.
It requests the user password and cannot be affiliated with any hacking tool.
Both GUI and CLI executables are provided, to be used in script environment or directly by user.
After each decipher operation, the result plain file is compared to original plain file by a digest method (or by size in new HBS files >2.1).

# Compatibility:

As a JAVA tool, this tool should be compatible with a large variety of OS, as long as a JRE 7+ is installed and configured with Unlimited JCE (a simple copy&past).

Requirements:
- At least 512 MB of system memory. Recommended minimum is 1 GB.
- A modern operating system. Both x86 and x64 are supported.
- Oracle JAVA JRE 7+, can be found here:
http://www.oracle.com/technetwork/java/index.html
or OpenJDK 7+, can be found here:
http://openjdk.java.net/	
- Unlimited JCE policy for your JAVA version, can be found here:
JAVA 7 : http://www.oracle.com/technetwork/java/ ... 32124.html
JAVA 8 : http://www.oracle.com/technetwork/java/ ... 33166.html
WARNING: without it JAVA cannot use AES 256 (used by Hybrid Backup Sync) so this tool cannot work. After each JAVA update, JCE policy must be re-applied.
- Tested on Windows 10 64bits, CentOS 6 32 bits, Oracle JRE 7 and Oracle JRE 8

IMPORTANT NOTES FOR MAC USERS :
- for password field, use Ctrl+C / Ctrl+V to copy and past.
- for JCE, change in 2 locations :
JRE: /Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/jre/lib/security
JDK: /Library/Java/JavaVirtualMachines/jdk1.x.x_xxx.jdk/Contents/Home/jre/lib/security

# How to decipher a file (summarized):

Pre. You need to download files from your provider to access them locally. Executable must be unzipped

In CLI :
1. Go to the current tool folder
2. use command line :
java -jar hybrid_backup_sync_decipher_XXX.jar -i PATH_FILE_TO_DECIPHER -o PATH_PLAIN_FILE (where XXX is the current version).
You will be ask for the password, or you can provide it with '-p' option. You can add verbose mode with '-v'.

In GUI (require hbs_decipher_gui project) :
1. Go to the current tool folder
2. use command line :
java -jar hybrid_backup_sync_decipher_XXX_gui.jar (or start it from your file explorer)
3. Choose a source and destination files
4. Start deciphering.
5. A dialog show you the result and more informations are available in HBSUtility_report.txt in destination folder.

Note : you can choose a folder as source or destination.
If a folder is chosen as source, the destination MUST be a folder too.
If a folder is chosen as destination but the source is a file, a file with the same name will be created in destination folder.
If the source and the destination are the same file or folder, a new file will be created, with same name prefixed by "plain_".

# Version

Compiled version 1.1 can be found here (with sources and GUI included too) :
https://mega.nz/#!bIBDDJjT!WmQB5idA7Rezzup7lU-k-5sAys14fQJGAvJJv2nRGrQ