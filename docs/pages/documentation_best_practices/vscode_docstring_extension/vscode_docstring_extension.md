---
title: Visual Studio Docstring Extension
nav_order: 1
parent: Documentation Best Practices
---

# Visual Studio Docstring Extension
{:.no_toc}

* TOC
{:toc}

While it's perfectly possible to do docstring formatting manually, the `autoDocstring` Visual Studio Code extension can be helpful for automatic formatting.

## Demo

This gif demonstrates the power of using `autoDocstring` (note that this is not the NumPy format and is for demonstration purposes only):

![Demonstration of the autoformatting from `autoDocstring`](../../../assets/images/vscode_extension/autodocstring_demo.gif)

To automatically insert the docstring with proper formatting, you type three quotes, `"""` like a normal docstring, then hit <kbd>Enter</kbd> to let the extension automatically format the docstring.

## How To Install

To get this extension:

1. Open Visual Studio Code.
2. Click the button on the far left menu that looks like 4 squares with one square being disconnected from the others. This is the extension tab.
3. Search "autoDocstring" in the search bar.
4. Click install. This automatically enables the autoDocstring extension.
5. Type, <kbd>Ctrl + Shift + P</kbd> to open the Visual Studio Code Command Palette.
6. Search for "Preferences: Open User Settings" and hit <kbd>Enter</kbd>.
7. In the search bar for extensions, search for "autoDocstring" and hit <kbd>Enter</kbd>.
8. Under the "Auto Docstring: Docstring Format" setting, select the NumPy docstring format.

