This document describes how to use the multiple cursor/multiple selection functionality being added to Brackets Sprint 38. Once it's released, this will move to [How to Use Brackets](https://github.com/adobe/brackets/wiki/How-To-Use-Brackets).

If you're an extension developer looking for tips on how to make your extension with multiple selections, see the [Brackets CodeMirror v4 Migration Guide](https://github.com/adobe/brackets/wiki/Brackets-CodeMirror-v4-Migration-Guide).

## Basic usage

Multiple selections are useful when you want to apply the same edit to different parts of your document. For example, you might want to add the same text to multiple nearby lines, or you might want a quick way to replace all the instances of a variable without having to use the Find bar.

There are two basic ways to create multiple selections:

* **Column/Rectangular selection**: Hold down the Alt key, then click and drag vertically or diagonally. Dragging vertically will result in cursors being added to each line you drag across. Dragging diagonally will select a rectangular block of text (which is really a set of selections, one on each line).
    * As a quick shortcut for creating multiple cursors vertically, you can use Shift-Alt-Up/Down to add a cursor above or below the current selection.
* **Discontiguous selection**: Make a selection, then hold down the Ctrl key (Windows) or Cmd key (Mac) and make another selection. The second selection will be added as another selection range.

You can also combine these techniques - hold down Ctrl-Alt or Cmd-Alt and then drag to add a column/rectangular selection to the existing multiple selection.

Once you have a multiple selection, most navigation commands and edits will apply to each cursor or range selection. For example, if you type, the characters you type will appear at each cursor (or replace each selection). The arrow keys will move each selection in the direction of the arrow.

Some commands, such as code hints and Quick Edit, only operate on one selection. These commands will always operate on the last selection you added (known as the "primary selection").

If you make a mistake while adding to the multiple selection, you can use Ctrl-U/Cmd-U to undo the last selection change. This is useful outside of multiple selections, too - you can use it to quickly jump back to the last selection you made, for example. The selection undo stack includes the edit undo stack, so if you undo selections back to your last edit point, then undo selection again, it will undo the edit. You can also use Ctrl-Shift-U/Cmd-Shift-U to redo selections.

You can hit Esc in order to get rid of a multiple selection, leaving only the primary selection selected.

## Searching with multiple selections

When coding, it's often useful to be able to quickly change multiple instances of the same string, like a variable name. You can use the Find bar to do this, but there's a quicker way to do it using multiple selections that can be more convenient in some cases.

Ctrl-B/Cmd-B (Add Next Match to Selection) will add the next instance of the currently selected range to the selection - it's kind of like Find Next, but uses the current selection and adds to the multiple selection. (If the current selection is a cursor, it will just expand to the surrounding word - hitting it again will then add the next instance of that word.) You can use this to quickly find the instances of the string you want to replace. Once you have all the instances selected, you can just type the replacement, and it will replace all the instances.

If you want to skip an instance, you can use Ctrl-Shift-B/Cmd-Shift-B (Skip and Add Next Match). That will remove the last-added instance from the selection and add the next instance. If you make a mistake or go too far, you can use Ctrl-U/Cmd-U to undo the last selection change.

If you know you want to replace all the instances in the document, you can use Alt-F3 (Windows) or Cmd-Ctrl-G (Mac) (Find All and Select) to select all matches for the current selection in the document.

## Shortcut reference

Here's a table of all the gestures related to multiple selection.

| Shortcut | Function |
| -------- | -------- |
| Alt-Click-Drag | Create a vertical or rectangular selection |
| Ctrl/Cmd-Click / Ctrl/Cmd-Click-Drag | Add a cursor or range to the selection |
| Shift-Alt-Up/Down | Add Line to Selection - adds a cursor on the previous/next line |
| Ctrl/Cmd-Alt-L | Split Selection into Lines - takes a contiguous selection and converts it to a multiple selection, one range for each line |
| Ctrl/Cmd-B | Add Next Match to Selection - adds the next match for the current range or word to the selection |
| Ctrl/Cmd-Shift-B | Skip and Add Next Match - removes the current range from the selection and adds the next match |
| Alt-F3 / Cmd-Ctrl-G | Find All and Select - adds all matches for the current range or word to the selection |
| Ctrl/Cmd-U | Undo Selection - undoes the last selection change or edit |
| Ctrl/Cmd-Shift-U | Redo Selection - redoes the last selection change or edit |
| Esc | Switch to Single Selection |