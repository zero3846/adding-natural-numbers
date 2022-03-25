# Leaf-Root-Branch Order

Date: 2022-03-22

Tags: design

Imagine you have a hierarchical menu, and you wanted to list out every endpoint with the full path to get there.
How would you do it?
Let's use the following menu structure:

Parent | Name
--- | ---
| File
| Edit
| View
| Help
File | New File
File | Open File
File | Save
File | Save As
File | Exit
Edit | Find
Edit | Find Next
Edit | Replace
Edit | Convert
Convert | Tabs to Spaces
Convert | Spaces to Tabs
Convert | Use DOS/Windows EOL
Convert | Use Unix/Linux EOL
Convert | Use Mac EOL
View | Show whitespace
View | Show End-of-lines
View | Zoom In
View | Zoom Out
Help | Index
Help | About

Obviously, the above format doesn't make it all that evident which features are where.
It especially isn't obvious which entries are leaf nodes.
Let's try again.

- File > New File
- File > Open File
- File > Save
- File > Save As
- File > Exit
- Edit > Find
- Edit > Find Next
- Edit > Replace
- Edit > Convert > Tabs to Spaces
- Edit > Convert > Spaces to Tabs
- Edit > Convert > Use DOS/Windows EOL
- Edit > Convert > Use Unix/Linux EOL
- Edit > Convert > Use Mac EOL
- View > Show whitespace
- View > Show End-of-lines
- View > Zoom In
- View > Zoom Out
- Help > Index
- Help > About

This is better.
It's clear what's a submenu, and what's a function.
It even shows you the order in which a user navigates the menu to get to a function.
The only problem is that it's hard to read what the function actually is.
The function names aren't at all aligned, and even if you were to put them in a separate column, you still have to move your eyes past a lot of repetitive prefixes.

What might be better is to simply move the function names (the leaf nodes) to the front.
The rest of the line can still be in root-to-leaf order, except the leaves were moved to the front, so it's technically leaf-root-branch order.

- **New File** : File
- **Open File** : File
- **Save** : File
- **Save As** : File
- **Exit** : File
- **Find** : Edit
- **Find Next** : Edit
- **Replace** : Edit
- **Tabs to Spaces** : Edit > Convert
- **Spaces to Tabs** : Edit > Convert
- **Use DOS/Windows EOL** : Edit > Convert
- **Use Unix/Linux EOL** : Edit > Convert
- **Use Mac EOL** : Edit > Convert
- **Show Whitespace** : View
- **Show End-of-lines** : View
- **Zoom In** : View
- **Zoom Out** : View
- **Index** : Help
- **About** : Help

Note that I went ahead and put emphasis on the function names.
I mostly didn't want to have copy and paste again to make a point, but if I tried to do that on the previous root-to-leaf order, it wouldn't have helped much.
At least here, the emphasized names are all aligned.
In fact, the menu paths become less important, but no less informative.

This type of order would be most useful if you had a list like this populating a search dropdown.
The leaf nodes are typically the most important thing, but the path from the root to the leaf's immediate parent still provide important context.



