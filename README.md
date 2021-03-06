# ExcelDarkThemeFix
Fixes Microsoft Excel appearance when custom Windows theme is used.

![preview](https://user-images.githubusercontent.com/34414488/90824725-8828aa80-e340-11ea-82db-ef3a5a36ed0e.png)

When the custom dark Windows theme is used, sheets, graphics items, charts and everything that have an "Automatic color" are displayed, exported and printed in the wrong colors.

This happens because Excel picks system colors *(instead of using predefined ones)* for the "Automatic color" which are altered by the themes.

This Add-In aims to fix this issue by setting colors to normal.

# What is fixed?

1. Sheets
1. Cells
1. Shapes
1. Charts - except slightly different font colors
1. Styles
1. Fixing multiple files in one click

# What has workaround?

1. Charts' font colors - there's an option to set it to black.
1. Cell's dark background when editing - there's an option to fix it, but you won't be able to undo anything. As an alternative, use the formula thingy right above the sheet to see what you type.
1. Mixed cells' fill outside of used range - fill can be either preserved (including an actual automatic color, default behavior) or removed completely. There's an to tweak it.

Enabling these options is described under the "Configuration" section.

# What is not fixed?

1. SmartArt - as far as I've tried, unfixable.
1. Automatic color replacement - will make things undoable and heavily slow down Excel (if not make it unusable).
1. Table styles - hard to fix and default styles don't need it.
1. Altering backgrounds - using background is a part of the fix. There's no way of detecting whether the sheet has a background, so scipt just will replace it.
1. You name it, I'm not an Excel expert :D

If you know how to fix any of these things, please, let me know. I will greatly appreciate your effort!

# Compatibility list

Fully compatible with Microsoft Office 2019. Should work in Office 2016 and 360.

If you can test it with Office versions other than 2019, please, fill out an issue and I'll update this list.

# Installation

Basically, you just need to install an Add-In. You can either stick to the instructions below or google a better guide.

1. Download `ExcelDarkThemeFix.xlam` and `whitebg.png` files.
1. "Unblock" Add-In:
   1. Move the cursor over `ExcelDarkThemeFix.xlam`, click right mouse button and click "Properties".
   1. At the bottom of the window find "Unblock" checkbox and check it. Then click "OK".
   1. If you don't have this option, please, proceed to the rest of the steps.
1. Navigate to `%AppData%\Microsoft\AddIns` and put the downloaded files here.
1. Enable macros:
   1. Open Excel.
   1. Navigate to "Options".
   1. On the left side of the window click "Customize Ribbon".
   1. On the right side of the window check "Developer" and "Add-Ins" boxes.
   1. Click "Ok" and restart Excel.
1. Enable this Add-In:
   1. Open "Developer" tab.
   1. Click on "Excel Add-Ins".
   1. Check the "ExcelDarkThemeFix" box.
   1. Click "Ok" and restart Excel.
1. If Add-In doesn't work:
   1. If you have an antivirus:
      1. Add `ExcelDarkThemeFix.xlam` to the exceptions. Some antiviruses might prevent Add-Ins from running. Don't worry, this Add-In won't make you computer explode :p Check the sources if you're unsure.
      1. Restart Excel and see if Add-In now works. If yes, you don't need to complete the steps below.
   1. Navigate to "Options".
   1. On the left side of the window click "Trust Center".
   1. Click "Trust Center Settings..."
   1. Now you've got three options:
      1. Unblock from PowerShell (try this first):
         1. Open PowerShell.
         1. Type `Unblock-File -Path "AppData\Roaming\Microsoft\AddIns\ExcelDarkThemeFix.xlam"` and hit Enter.
         1. Close PowerShell.
      1. Trust only installed Add-Ins (recommended):
         1. On the left side of the window click "Trusted new locations".
         1. Click "Add Location".
         1. Click "Browse..."
         1. Navigate to "%AppData%\Microsoft\AddIns" and click "OK".
         1. Click "OK" in all opened windows.
      1. Trust EVERY Add-In you open:
         1. On the left side of the window click "File Block Settings".
         1. Find "Excel 2007 and later Add-In files" row and uncheck both of the checkboxes. Well, you may uncheck all the rows to make your life easier.
         1. Click "OK" in all opened windows.
   1. Restart Excel.

# Usage

Script does everything automatically. However, if you've set automatic colors to something and don't want to fix it yourself, in Excel:

1. Open "Add-Ins" tab (if you didn't have it, it will be added automatically).
1. Click "Fix all open workbooks".
1. Read text in pop-up dialog. It says that if you click "Yes", you won't be able to undo the changes you've made. The only way to undo something is to close all workbooks without saving and open them again.
1. Click "Yes" if you will not need to undo anything.

# Configuration

This Add-In provides some cool but unsafe options that you can enable. In order to do this, in Excel:

1. Open "Developer" tab.
1. Click on "Visual Basic".
1. On the left pane, navigate to element displayed on the following screenshot and double-click on it:

![Open "ExcelDarkThemeFixModule"](https://user-images.githubusercontent.com/34414488/90905218-8ad6de80-e3d8-11ea-8369-9ebb11ffafca.png)

You'll see some code. Don't freak out, just follow the instructions in it. Read everything **carefully**!

When you're done, press `Ctrl+S` and restart Excel.

# FAQ

### Do I need it if I use light theme?

**Yes**, if your theme uses colors different from white for window and black for text. It is recommended to **always use this Add-In with custom themes** since one usually doesn't checks the colors.

### Does it work with high contrast themes?

No.
*Note: this question is **NOT** about high contrast **looking** themes (they're working fine) but about an actual Windows' feature.*

### Can I disable pop-up dialog when I press "Fix All" button?

Yes, there's an option for it, see "Configuration" section.

### Can you make a theme for Excel or other MS Office applications?

No. *It's almost (if not entirely) impossible because there's no way of tracking which cell should use which colors. Same goes for every MS Office application.*

### I have a problem or found a bug. Where can I report it?

Please, fill out an issue on this repository. Please, provide as much information as possible.

### How can I help?

If you're regular user, you can test this Add-In with different kinds of workbooks and report found issues. You could also install an older version of Microsoft Office and check if this Add-In is compatible with it.

You can also spread the word about this Add-In (especially in non-English speaking parts of the Internet), so other people could have a less of a headache.

If you're developer, you can add some useful features or fix things described above. Start by thoroughly reading the code to understand what it does. Then do the coding. When you're done, create a pull request with your code. If it's not hard, please, provide the code in plain text instead of .xlam file even if you've changed entire script.
