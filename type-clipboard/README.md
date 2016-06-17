It "types" the contents of the clipboard.

Why can't you just paste the contents you ask?  Sometimes pasting just doesn't work.
* One example is in system password fields on OSX.
* Sometimes you're working in a VM and the clipboard isn't shared.
* Other times you're working via Remote Desktop and again, the clipboard doesn't work in password boxes such as the system login prompts.
* Connected via RDP and clipboard sharing is disabled and so is mounting of local drives.  If the system doesn't have internet access there's no easy way to get things like payloads or Powershell scripts onto it... until now.

The Windows version is written in AutoHotKey and easily compiles to an executable.  It's a single line script that maps Ctrl-Shift-V to type the clipboard.

```ahk
^+v::Send %Clipboard%
```

The Mac version is writtern in AppleScript.

```applescript
tell application "System Events" to keystroke the clipboard as text
```

The equivalent one-liner from the command line would be:

```bash
osascript -e 'tell application "System Events" to keystroke the clipboard as text'
```

To bind this to a keyboard shortcut you have several options.  Sticking with builtin OSX utilities you can follow this guide.
- http://blog.fosketts.net/2010/08/09/assign-keyboard-shortcut-applescript-automator-service/

Otherwise, you can use a third party program that lets you set custom hotkeys such as: BetterTouchTool, Keyboard Maestro, or Hammerspoon
