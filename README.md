<h2><code>explorer.exe</code>: Long Path Awareness <br/><sub>(..also with new <code>SegmentHeap</code>)</sub></h2>

<h1>

```diff
- -------------------------------- -
- warning: no support!             -
- you are doing this on your-own!  -
- -------------------------------- -
```

</h1>

0. download repository, unzip.
1. unzip zipped files.
2. open each reg and manifest file with notepad2 or notepad++, make sure its end-of-line character is Windows-EOL (`\r\n`).
3. you will need a 3rd-party file manager. I'm using FAR-Manager. Total-commander is fine too.
4. copy the explorer manifest-files to their locations, rename them to `explorer.exe.manifest`.
5. `WindowsShell.Manifest` is locked, used FAR-manager (run as admin), rename it to something else, copy the modified manifest, rename it to `WindowsShell.Manifest` .
6. apply two registry patches.
7. Windows has a glitch, in addition to applying registry patch to opt-in long-path awareness you need group policy.

```txt
Start » Run » gpedit.msc
Local Computer Policy
» Computer Configuration
» Administrative Templates
» System
» Filesystem
Enable Win32 long paths » change from "Not Configured" to "Enabled", [OK].
```

older build might also have this (switch it ON as well):  

```txt
Start » Run » gpedit.msc
Local Computer Policy
» Computer Configuration
» Administrative Templates
» System
» Filesystem
» NTFS
Enable NTFS long paths » change from "Not Configured" to "Enabled", [OK].
```

8. reboot. 
9. done.
10. to uninstall remove the `explorer.exe.manifest` and the modified `WindowsShell.Manifest`, and restore the original `WindowsShell.Manifest`. reboot.

