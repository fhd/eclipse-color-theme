Eclipse Color Theme
===================

Color themes for Eclipse.

**Please note: The repository has been moved to [http://github.com/eclipse-color-theme/eclipse-color-theme](http://github.com/eclipse-color-theme/eclipse-color-theme) and this one is no longer updated.**

Eclipse Color Theme makes it possible to switch color themes
conveniently and without side effects. Support for importing themes is
planned.

You can install the plugin from the
[update site](http://fhd.github.com/eclipse-color-theme).  After
installing, go to *Window->Preferences->General->Appearance->Color
Theme* to change the color theme.

When updating the plugin via Eclipse, go to the preferences page and
press *OK* once, otherwise you won't see any changes. We're planning
to fix this.

Rationale
---------

While Eclipse allows you to change the syntax coloring in great
detail, there is no support for managing multiple color themes. It is
possible to achieve that by importing and exporting preferences files,
but this is inconvenient and likely to mess up your preferences.
Furthermore, color themes have to be created for every single editor,
a theme for the Java editor does not change the XML, JavaScript or
any other editors. This plugin solves these issues by mapping a
generic color theme format to specific preferences entries for each
supported editor.

Editors and themes
------------------

Eclipse Color Theme currently supports the following editors:

* Text
* Java
* Java properties
* XML
* HTML
* CSS
* JavaScript
* C++
* PHP
* Ant
* SQL

Available themes:

* [Inkpot](http://www.vim.org/scripts/script.php?script_id=1143)
* [Zenburn](http://slinky.imukuppi.org/zenburnpage/)
* [Vibrant Ink](http://code.google.com/p/vibrant-ink-textmate/)
* [Oblivion](http://www.rogerdudler.com/?p=362)

Adding a theme
--------------

To create a new theme, you'll have to get the source and build the
plugin until theme importing/exporting is implemented.

Create an XML file in the *com.github.fhd.eclipsecolortheme.themes*
package next to *zenburn.xml* and change the colour values until
you're satisfied. Then add the file name to the constant `FILE_NAMES`
in `ColorThemeManager`.

The keys are quite Java-specific right now, but the entries are mapped
to other editors (e.g. the *method* key is used for XML/HTML tags). To
see all possible keys, have a look at the constants in
`ColorThemeKeys`.

Adding an editor
----------------

If you would like to add an editor, proceed as follows:

1. Go to the *syntax coloring* preferences page of the editor,
e.g. *C/C++->Editor->Syntax Coloring*.

2. Look at the colour theme keys of one theme (I suggest you use
Zenburn for that) in this plugin's `ColorThemeManager` class and set
up the syntax colouring using the colours defined there.

3. Open the editor's preferences file, e.g. *workspace/.metadata/.plugins/org.eclipse.core.runtime/.settings/org.eclipse.cdt.ui.prefs*
and create a new subclass of `ThemePreferenceMapper` where you map the
colour theme's keys to those of the editor.

License
-------

Copyright (C) 2011 Felix H. Dahlke and Roger Dudler

This is open source software, licensed under the Eclipse Public
License. See the file COPYING for details.
