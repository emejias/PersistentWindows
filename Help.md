

## PersistentWindows Quick Help
### Command Line Options
  | Command line option | Meaning |
  | --- | --- |
  | -delay_start 10 | Delay the application startup by 10 seconds. Useful if PersistentWindows autostart fails to show the icon because of Windows Update.
  | -redirect_appdata | Use the current directory instead of the User AppData directory to store the database file. This option is also useful for launching multiple PersistentWindows instances.
  | -gui=0 | Do not display the PersistentWindows icon on the System Tray. Effectively runs PersistentWindows as a service
  | -splash=0       | No splash window at PersistentWindows startup
  | -notification=1 | Turn on balloon tip and sound notification when restoring windows
  | -silent         | No splash window, no balloon tip hint, no event logging
  | -ignore_process "notepad.exe;foo" | Avoid restoring windows for the processes notepad.exe and foo
  | -debug_process "notepad.exe;foo" | Print window positioning event logs for the processes notepad.exe and foo in event viewer
  | -prompt_session_restore | Ask the user before restoring the window layout upon resuming the last session. This may help to reduce the total restore time for remote desktop sessions on slow internet connections.
  | -delay_auto_capture 1.0 | Adjust the latency from window move event to auto-capture to 1.0 second, the default latency is 3~4 seconds.
  | -delay_auto_restore 2.5 | Adjust the latency from monitor on/off event to auto-restore to 2.5 seconds (the default latency is 1 second), in case some monitor fails to go to sleep due to auto-restore starts too early.
  | -slow_restore | Slow down the auto-restore progress to avoid incomplete restore due to adversarial moves by Windows OS
  | -redraw_desktop | Redraw the whole desktop after a restore in case some window workarea is not refreshed
  | -fix_zorder=1   | Preserve window Z-order for automatic restore. The Z-order of a window indicates the window's position in a stack of overlapping windows.
  | -fix_offscreen_window=0 | Turn off auto correction of off-screen windows
  | -fix_unminimized_window=0 | Turn off auto restore of unminimized windows. Use this switch to avoid undesirable window shifting during window activation, which comes with Event id 9999 : "restore minimized window ...." in event viewer.
  | ‑auto_restore_missing_windows=1 | When restoring from disk, restore missing windows without prompting the user
  | ‑auto_restore_missing_windows=2 | At startup, automatically restore missing windows from disk. The user will be prompted before restoring each missing window
  | ‑auto_restore_missing_windows=3 | At startup, automatically restore missing windows from disk without prompting the user
  | -invoke_multi_window_process_only_once=0 | Launch an application multiple times when multiple windows of the same process need to be restored from the database.
  | -check_upgrade=0 | Disable the PersistentWindows upgrade check
  | -auto_upgrade=1 | Upgrade PersistentWindows automatically without user interaction

---

### Shortcuts To Capture/Restore Snapshots
  | Snapshot command | Shortcut|
  | --- | --- |
  | Capture snapshot 0 | Double click the PersistentWindows icon
  | Restore snapshot 0 | Click the PersistentWindows icon
  | Capture snapshot X | Double click the PersistentWindows icon,  then immediately press key X (X represents a digit [0-9] or a letter [a-z])
  | Restore snapshot X | Click the PersistentWindows icon, then immediately press key X
  | Undo the last snapshot restore | Alt + click the PersistentWindows icon

---
### Other Features
* Save a named capture to disk:
  * Ctrl click the "Capture windows to disk" menu option, then enter a name in the pop-up dialog

* Restore a named capture from disk:
  * Ctrl click the "Restore windows from disk" menu option, then enter the saved name in the dialog

* Run PersistentWindows with custom icons:
  * Save your icon file as `pwIcon.ico` and copy it to `C:/Users/\<YOUR_ID>/AppData/Local/PersistentWindows/`, or copy it to the current directory if running PersistentWindows with the `-redirect_appdata` command line option.
  * Save the second icon file as `pwIconBusy.ico`. This icon is displayed when PersistentWindows is busy restoring windows.

* Manipulate the window z-order:
  * Bring a window to the top of the z-order by clearing the topmost flag of an obstructive window:
    * Click on the other window first to de-focus, then Ctrl click the window that you want to bring to the top (or the corresponding icon on the taskbar).
  * Send a remote desktop or vncviewer window to the bottom of the z-order (because the Alt+Esc hotkey may not work for them on Windows 7 or old Windows 10 versions):
    * De-focus the rdp window first, then hold Ctrl+Win and click on the rdp window

* Enable/Disable auto restore for any (child or dialog) window:
  * To add a window for auto capture/restore, move the window using the mouse
  * To remove a window from auto capture/restore, hold Ctrl+Shift then move the window
```
