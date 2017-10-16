---
title: Sublime text 3 插件 OmniMarkupPreviewer
date: 2017-10-16 10:50:55
tags: Sublime
categories: 软件
photos: 
---

    这是一个Sublime里非常好用的插件。可以在编辑好MarkDown文件后快速预览，以及导出HTML文件。  
    但今天我发现开启Hexo本地服务器后直接编辑保存文件也可在浏览器中刷新后查看效果。非常好用。

Package Control Messages
========================

OmniMarkupPreviewer
-------------------

  OmniMarkupPreviewer  
  ===================
  
  OmniMarkupPreviewer is a plugin for both [Sublime Text 2] and [Sublime Text 3]
  that preview markups in web browsers. OmniMarkupPreviewer renders markups into
  htmls and send it to web browser in the backgound, which enables a live preview.
  Besides, OmniMarkupPreviewer provide support for exporting result to
  html file as well.
  
  [Sublime Text 2]: http://www.sublimetext.com/2
  [Sublime Text 3]: http://www.sublimetext.com/3
  
  OmniMarkupPreviewer has builtin support following markups:
  
  * [Markdown](http://daringfireball.net/projects/markdown/)
  * [reStructuredText](http://docutils.sourceforge.net/rst.html)
  * [WikiCreole](http://wikicreole.org/)
  * [Textile](http://www.textism.com/tools/textile/)
  * [Pod](http://search.cpan.org/dist/perl/pod/perlpod.pod) (Requires Perl >= `5.10`
    and can be found in `PATH`, if the perl version < `5.10`, `Pod::Simple` should be
    installed from `CPAN`.)
  * [RDoc](http://rdoc.sourceforge.net/) (Requires ruby in your `PATH`)
  
  
  Usage
  -----
  
  ### Key Bindings
  
  The default key bindings:
  
  **Windows, Linux:**
  
  * <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>O</kbd>: Preview Markup in Browser.
  * <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>X</kbd>: Export Markup as HTML.
  * <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>C</kbd>: Copy Markup as HTML.
  
  **OSX:**
  
  * <kbd>⌘</kbd>+<kbd>⌥</kbd>+<kbd>O</kbd>: Preview Markup in Browser.
  * <kbd>⌘</kbd>+<kbd>⌥</kbd>+<kbd>X</kbd>: Export Markup as HTML.
  * <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>C</kbd>: Copy Markup as HTML.
  
  
  ### Command Palette
  
  Available OmniMarkupPreviewer commands in the command palette:
  
  * `OmniMarkupPreviewer: Preview Current Markup in Browser`
  * `OmniMarkupPreviewer: Export Current Markup as HTML`
  * `OmniMarkupPreviewer: Empty Cache`
