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

## Current Design Patterns

This section documents the patterns currently in use across the wiki. Follow these when adding new pages.

### File & Directory Organization

- **Root level**: `Main_Page.mediawiki` and category index pages (e.g., `Highlighted_work.mediawiki`).
- **Subdirectories**: Individual articles grouped by category in lowercase-hyphenated directories (e.g., `highlighted-work/`).
- **File naming**: Underscores for spaces, colons preserved. Example: `Towards_Monosemanticity:_Decomposing_Language_Models_With_Dictionary_Learning.mediawiki`.

### Current Directory Structure

```
.
├── CLAUDE.md
├── README.md
├── Main_Page.mediawiki
├── Highlighted_work.mediawiki
├── Architectures_for_interpretability.mediawiki
├── Concepts.mediawiki
├── Communities.mediawiki
├── People_and_groups.mediawiki
├── Phenomena.mediawiki
├── Methods.mediawiki
├── methods/
│   └── Dictionary_learning.mediawiki
├── architectures-for-interpretability/
│   └── Sparse_autoencoder.mediawiki
├── concepts/
│   └── Feature.mediawiki
├── highlighted-work/
│   ├── Progress_measures_for_grokking_via_mechanistic_interpretability.mediawiki
│   └── Towards_Monosemanticity:_Decomposing_Language_Models_With_Dictionary_Learning.mediawiki
├── communities/
│   └── Mech_Interp_discord.mediawiki
├── people-and-groups/
│   └── Neel_Nanda.mediawiki
└── phenomena/
    └── Grokking.mediawiki
```

### Page Hierarchy

```
Main_Page.mediawiki                          (hub — links to all categories)
  └─ Highlighted_work.mediawiki              (category index page, root level)
       └─ highlighted-work/                  (subdirectory, lowercase-hyphenated)
            └─ Towards_Monosemanticity:_Decomposing_Language_Models_With_Dictionary_Learning.mediawiki
```

Concrete example of how these files connect:

- `Main_Page.mediawiki` links to the category: `[[:Category:Highlighted work|Highlighted work]]`
- `Highlighted_work.mediawiki` (root level) is the index page. It transcludes articles:
  ```
  * {{:Towards Monosemanticity: Decomposing Language Models With Dictionary Learning}}
  ```
- `highlighted-work/Towards_Monosemanticity:_....mediawiki` (subdirectory) is the article. Its summary is wrapped in `<onlyinclude>` for transclusion, and it ends with `[[Category:Highlighted work]]`.

### Standard Article Structure

Every article page follows this layout:

```
<onlyinclude>
Summary paragraph with inline <ref> citations.
</onlyinclude>
More text.

== References ==

<references />

[[Category:Category Name]]
```

- **`<onlyinclude>`** wraps only the summary so index pages can transclude a short description. Author and publication metadata goes **after** the closing `</onlyinclude>` tag so it does not appear in transclusions.
- **References section** comes after the metadata, using `<references />`.
- **Category assignment** is always the last line of the file.

### Transclusion for Index Pages

Category index pages list articles using full-page transclusion:

```
* {{:Article Title}}
```

Because articles use `<onlyinclude>`, only the summary paragraph is pulled in. This keeps index pages automatically up to date with article content.

### Reference / Citation Format

References use Wikipedia-style Citation Style 1 (CS1) plain-text formatting inside `<ref>` tags. Use periods (`.`) to separate fields. Titles of articles and pages go in double quotes, linked to the URL. Titles of journals, websites, and conference proceedings go in italics (`''...''`).

**Web page:**

```
<ref>Last, First (YYYY-MM-DD). [https://example.com "Title"]. ''Website''.</ref>
```

**arXiv paper:**

```
<ref>Last1, First1; Last2, First2 (YYYY). [https://arxiv.org/abs/ID "Title"]. arXiv:[https://arxiv.org/abs/ID ID].</ref>
```

**Journal article:**

```
<ref>Last1, First1; Last2, First2 (YYYY). [https://doi.org/DOI "Title"]. ''Journal''. '''Vol'''(Issue): Pages. doi:[https://doi.org/DOI DOI].</ref>
```

**Conference paper:**

```
<ref>Last1, First1; Last2, First2 (YYYY). [https://url "Title"]. ''Conference Name''. pp. Pages.</ref>
```

**Wiki/forum page:**

```
<ref>[https://example.com "Title"]. ''Site Name''.</ref>
```

**Rules:**

- Author names: `Last, First` format. Multiple authors separated by semicolons.
- For 4+ authors, list the first three and use `et al.`: `Last1, First1; Last2, First2; Last3, First3; et al.`
- Dates: `YYYY-MM-DD` for web pages with specific dates, `YYYY` for papers/journals.
- Volume numbers in bold: `'''42'''`.
- DOIs: `doi:[https://doi.org/DOI DOI]`.
- arXiv IDs: `arXiv:[https://arxiv.org/abs/ID ID]`.
- Use named refs when citing the same source multiple times: `<ref name="name">...</ref>` and `<ref name="name" />`.
- Keep using `<references />` to display all references.

### Category Taxonomy

The Main Page defines 17 top-level categories displayed in a full-width wikitable. When linking to a category from content (without adding the page to that category), use the colon prefix:

```
[[:Category:Name|Display Text]]
```

### Formatting Conventions

- **Bold** (`'''...'''`) is used to introduce key terms and abbreviations on first mention.
- **Clickable article titles**: The first bold mention of an article's own title in its `<onlyinclude>` summary must be a wikilink so it is clickable when transcluded on index pages. Use `'''[[Page Name]]'''` or `'''[[Page Name|display text]]'''`.
- Level 2 headings (`== ... ==`) only — level 1 is reserved for the page title.
- Blank lines separate sections and structural elements; no multiple consecutive blank lines.

##Additional rules

- Commit and push to GitHub after each change

- When updating @Main_Page.mediawiki, also update README.md and CLAUDE.md with same edits

- When adding anything from some source, make sure to as exactly quote words from the source as possible to not make stuff up, and add the source as a reference

- When using text word-for-word from a source, wrap it in quotation marks with the source citation immediately after (e.g., `"quoted text."<ref>Source.</ref>`). Change inner double quotes to single quotes when nested inside an outer quote.

## Contents of @Main_Page.mediawiki

# AI Interpretability Wiki

A local mirror of the [AI Interpretability Wiki](https://aiinterpretability.miraheze.org/), written in MediaWiki and hosted on Miraheze.

## About

**Interpretability** is the ability for the decision processes and inner workings of artificial intelligence and machine learning systems to be understood by humans or other outside observers. [[source](https://www.lesswrong.com/w/interpretability-ml-and-ai)]

**Mechanistic interpretability** (often abbreviated as **mech interp**, **mechinterp**, or **MI**) is a subfield of research within AI interpretability and explainable artificial intelligence that aims to understand the internal workings of neural networks by analyzing the mechanisms present in their computations. The approach seeks to analyze neural networks in a manner similar to how binary computer programs can be reverse-engineered to understand their functions. [[source](https://en.wikipedia.org/wiki/Mechanistic_interpretability)] "This can be contrasted to subfieds of interpretability which seek to attribute some output to a part of a specific input, such as clarifying which pixels in an input image caused a computer vision model to output the classification 'horse'." [[source](https://www.lesswrong.com/w/interpretability-ml-and-ai)]

## Contents

| Category | Description |
|----------|-------------|
| Highlighted work | Notable and influential work in AI interpretability |
| Concepts | Core ideas and terminology |
| Methods | Techniques and approaches used to interpret models |
| Architectures for interpretability | Architectures used to interpret models |
| Applications | Practical uses and deployments |
| Phenomena | Behaviors and properties analyzed |
| Theory | Theoretical foundations, mathematical and formal frameworks in AI and AI interpretability |
| AI architectures | Architectures of studied models |
| Interpretability architectures | Architectures that are designed to be more interpretable |
| Surveys | Survey papers and literature reviews |
| Github codebases | Code repositories |
| People and groups | Researchers, labs, and organizations |
| Communities | Communities on Discord, Slack, etc. |
| Feeds | Blogs, newsletters, and content feeds |
| Youtube channels | Video content and educational channels |
| Resources for learning | Tutorials, courses, and learning materials |
| Events | Conferences, workshops, and meetups |

## All pages

### Highlighted work

* Progress measures for grokking via mechanistic interpretability
* Towards Monosemanticity: Decomposing Language Models With Dictionary Learning

### Concepts

* Feature

### Methods

* Dictionary learning

### Architectures for interpretability

* Sparse autoencoder

### Phenomena

* Grokking

### People and groups

* Neel Nanda

### Communities

* Mech Interp discord

## Tips

* To check which pages link to the page you're on, go to the Tools menu on the top right and click on "What links here".
* To enable dark mode, log in, go to Preferences, Appearance, and select Dark. Alternatively, use the [Dark Reader](https://chromewebstore.google.com/detail/dark-reader/eimadpbcbfnmbkopoojfekhnkhdbieeh) Chrome extension, but it might be a bit broken.

## Random page

[Click here to go to a random page on the wiki!](https://aiinterpretability.miraheze.org/wiki/Special:Random)

## Wiki created by

* Burny ([website](https://burnyverse.com/), [X](https://x.com/burny_tech), [GitHub](https://github.com/BurnyCoder), [LinkedIn](https://www.linkedin.com/in/libor-burian-1113b0207/), [Facebook](https://www.facebook.com/burian.libor/), [Telegram](https://t.me/burnytech), [BlueSky](https://burnytech.bsky.social), [Mastodon](https://mathstodon.xyz/@Burny), Discord: burnytech, [burian.lib@gmail.com](mailto:burian.lib@gmail.com)).
