This is a local mirror of the AI Interpretability Wiki, written in MediaWiki and hosted on Miraheze.

## If you don't know, search the web

When unsure about MediaWiki syntax, templates, extensions, Miraheze-specific features, or any wiki-related topic, **always search the web** before guessing. Key references:

- MediaWiki Cheatsheet: https://www.mediawiki.org/wiki/Cheatsheet
- Help:Formatting: https://www.mediawiki.org/wiki/Help:Formatting
- Help:Wikitext: https://en.wikipedia.org/wiki/Help:Wikitext
- Miraheze Meta: https://meta.miraheze.org/

## MediaWiki Page Format Guide

Pages use **wikitext** markup. Below is a reference for the most common syntax.

### Text Formatting

```
''italic''
'''bold'''
'''''bold & italic'''''
<u>underline</u>
<s>strikethrough</s>
<code>inline code</code>
<sub>subscript</sub>
<sup>superscript</sup>
```

### Headings

Skip level 1 (`= ... =`), it is reserved for the page title. Start with level 2:

```
== Level 2 ==
=== Level 3 ===
==== Level 4 ====
===== Level 5 =====
====== Level 6 ======
```

An article with 4 or more headings automatically creates a table of contents. Use `__NOTOC__` to suppress it.

### Paragraphs and Line Breaks

- Single line breaks are ignored; leave a blank line to start a new paragraph.
- Force a line break within a paragraph with `<br />`.

### Links

```
[[Page Name]]                          Internal link
[[Page Name|Display Text]]             Internal link with custom text
[[Page Name#Section]]                  Link to a section
[[:Category:Example]]                  Link to a category page
[[w:Article Name]]                     Interwiki link (Wikipedia)
[[mh:subdomain:Page]]                  Interwiki link (another Miraheze wiki)
[https://example.com Display Text]     External link
```

### Lists

```
* Bullet item                         Bulleted list
** Nested bullet                       Nested item
# Numbered item                        Numbered list
## Nested numbered                     Nested numbered
; Term                                 Definition list term
: Definition                           Definition list definition
: Indented text                        Indentation (use sparingly)
```

### Images and Files

```
[[File:Example.jpg]]                           Basic image
[[File:Example.jpg|thumb|Caption text]]         Thumbnail with caption
[[File:Example.jpg|thumb|200px|Caption text]]   Thumbnail with fixed width
```

### Tables

```
{| class="wikitable"
|+ Table caption
! Header 1 !! Header 2
|-
| Cell 1 || Cell 2
|-
| Cell 3 || Cell 4
|}
```

### Templates

```
{{Template Name}}                      Transclude a template
{{Template Name|param=value}}          Template with parameter
{{{parameter|}}}                       Parameter placeholder (in template source)
{{:Page Name}}                         Transclude a regular page
```

### Categories

```
[[Category:Category Name]]            Add page to a category (place at bottom of page)
[[:Category:Category Name]]           Link to a category without adding the page to it
```

### Redirects

```
#REDIRECT [[Target Page]]             Must be the first line of the page
```

### References / Citations

```
Claim.<ref>Source details here.</ref>  Inline citation
<references />                         Display all references (place in a == References == section)
```

### Preformatted Text and Code

```
<pre>Preformatted block (no wiki markup interpreted)</pre>
<nowiki>Escape ''wiki markup''</nowiki>
<syntaxhighlight lang="python">
def hello():
    print("Hello")
</syntaxhighlight>
```

A line starting with a space is rendered as preformatted text (monospace, no wrapping).

### Comments and Behavior Switches

```
<!-- This is a comment, invisible in rendered output -->
__NOTOC__              Suppress table of contents
__NOEDITSECTION__      Hide section edit links
{{DISPLAYTITLE:Title}} Override displayed page title
{{DEFAULTSORT:Key}}    Set default category sort key
```

### Special Template Tags (for template source pages)

```
<noinclude>Only shown on the template page itself</noinclude>
<includeonly>Only shown when the template is transcluded</includeonly>
<onlyinclude>Only this part is transcluded</onlyinclude>
```

### Horizontal Rule

```
----
```

### HTML

Some HTML is allowed in wikitext: `<div>`, `<span>`, `<code>`, `<blockquote>`, `<br />`, etc. Dangerous attributes like `onclick` are stripped.

## Contents of @Main_Page.mediawiki

== Welcome to {{SITENAME}} wiki! ==

'''Interpretability''' is the ability for the decision processes and inner workings of AI and machine learning systems to be understood by humans or other outside observers.

'''Mechanistic interpretability''' (often abbreviated as '''mech interp''', '''mechinterp''', or '''MI''') is a subfield of research within AI interpretability and explainable artificial intelligence that aims to understand the internal workings of neural networks by analyzing the mechanisms present in their computations. The approach seeks to analyze neural networks in a manner similar to how binary computer programs can be reverse-engineered to understand their functions.

== Contents ==

{| class="wikitable" style="width:100%;"
|-
! Category !! Description
|-
| [[:Category:Highlighted work|Highlighted work]] || Notable and influential work in AI interpretability
|-
| [[:Category:Concepts|Concepts]] || Core ideas and terminology
|-
| [[:Category:Methods|Methods]] || Techniques and approaches used to interpret models
|-
| [[:Category:Interpretability architectures|Interpretability architectures]] || Architectures and frameworks used for AI interpretability
|-
| [[:Category:Applications|Applications]] || Practical uses and deployments
|-
| [[:Category:Phenomena|Phenomena]] || Behaviors and properties analyzed
|-
| [[:Category:AI architectures|AI architectures]] || Architectures of models studied 
|-
| [[:Category:Theory|Theory]] || Theoretical foundations, mathematical and formal frameworks in AI and AI interpretability
|-
| [[:Category:Surveys|Surveys]] || Survey papers and literature reviews
|-
| [[:Category:Github codebases|Github codebases]] || Code repositories
|-
| [[:Category:People and groups|People and groups]] || Researchers, labs, and organizations 
|-
| [[:Category:Communities|Communities]] || Communities
|-
| [[:Category:Feeds|Feeds]] || Blogs, newsletters, and content feeds
|-
| [[:Category:Youtube channels|Youtube channels]] || Video content and educational channels
|-
| [[:Category:Resources for learning|Resources for learning]] || Tutorials, courses, and learning materials
|-
| [[:Category:Events|Events]] || Conferences, workshops, and meetups
|}
