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
├── Papers.mediawiki
├── Architectures_for_interpretability.mediawiki
├── Concepts.mediawiki
├── Communities.mediawiki
├── People_and_groups.mediawiki
├── Phenomena.mediawiki
├── Methods.mediawiki
├── AI_architectures.mediawiki
├── Theory.mediawiki
├── Surveys.mediawiki
├── Feeds.mediawiki
├── Github_codebases.mediawiki
├── Resources_for_learning.mediawiki
├── methods/
│   └── Dictionary_learning.mediawiki
├── architectures-for-interpretability/
│   └── Sparse_autoencoder.mediawiki
├── concepts/
│   └── Feature.mediawiki
├── papers/
│   ├── Progress_measures_for_grokking_via_mechanistic_interpretability.mediawiki
│   └── Towards_Monosemanticity:_Decomposing_Language_Models_With_Dictionary_Learning.mediawiki
├── communities/
│   └── Mech_Interp_discord.mediawiki
├── people-and-groups/
│   └── Neel_Nanda.mediawiki
├── ai-architectures/
│   ├── CNN.mediawiki
│   └── Transformer.mediawiki
├── github-codebases/
│   └── TransformerLens.mediawiki
├── feeds/
│   ├── Anthropic_Interpretability_research.mediawiki
│   └── Transformer_Circuits_Thread.mediawiki
├── theory/
│   ├── A_Mathematical_Framework_for_Transformer_Circuits.mediawiki
│   ├── The_Principles_of_Deep_Learning_Theory.mediawiki
│   └── Geometric_Deep_Learning:_Grids,_Groups,_Graphs,_Geodesics,_and_Gauges.mediawiki
├── surveys/
│   ├── Mechanistic_Interpretability_for_AI_Safety_--_A_Review.mediawiki
│   ├── Locate,_Steer,_and_Improve:_A_Practical_Survey_of_Actionable_Mechanistic_Interpretability_in_Large_Language_Models.mediawiki
│   └── An_Extremely_Opinionated_Annotated_List_of_My_Favourite_Mechanistic_Interpretability_Papers_v2.mediawiki
├── phenomena/
│   ├── Alignment.mediawiki
│   └── Grokking.mediawiki
└── resources-for-learning/
    ├── ARENA.mediawiki
    └── How_to_become_a_mechanistic_interpretability_researcher.mediawiki
```

### Page Hierarchy

```
Main_Page.mediawiki                          (hub — links to all categories)
  ├─ Highlighted_work.mediawiki              (category index page, root level)
  │    └─ papers/                            (subdirectory, lowercase-hyphenated)
  │         └─ Towards_Monosemanticity:_Decomposing_Language_Models_With_Dictionary_Learning.mediawiki
  └─ Papers.mediawiki                        (category index page, root level)
       └─ papers/                            (subdirectory, shared with Highlighted work)
            └─ Towards_Monosemanticity:_Decomposing_Language_Models_With_Dictionary_Learning.mediawiki
```

Concrete example of how these files connect:

- `Main_Page.mediawiki` links to the category: `[[:Category:Highlighted work|Highlighted work]]`
- `Highlighted_work.mediawiki` (root level) is the index page. It transcludes articles:
  ```
  * {{:Towards Monosemanticity: Decomposing Language Models With Dictionary Learning}}
  ```
- `papers/Towards_Monosemanticity:_....mediawiki` (subdirectory) is the article. Its summary is wrapped in `<onlyinclude>` for transclusion, and it ends with `[[Category:Highlighted work]]` and `[[Category:Papers]]`.

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
Description of the category.

* {{:Article Title}}

== References ==

<references />
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

The Main Page defines 18 top-level categories displayed in a full-width wikitable. When linking to a category from content (without adding the page to that category), use the colon prefix:

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

== Welcome to {{SITENAME}} wiki! ==

"Present-day [https://en.wikipedia.org/wiki/Artificial_intelligence artificial intelligence] and [https://en.wikipedia.org/wiki/Machine_learning machine learning] systems are typically not very transparent or interpretable. You can use a model's output, but the model can't tell you why it made that output. This makes it hard to determine the cause of biases in ML models."<ref name="lesswrong-interp">[https://www.lesswrong.com/w/interpretability-ml-and-ai "Interpretability (ML & AI)"]. ''LessWrong''.</ref>

'''Interpretability''' is "the broader subfield of AI studying why AI systems do what they do, and trying to put this into human-understandable terms."<ref name="nanda-glossary">[https://www.neelnanda.io/mechanistic-interpretability/glossary "Mechanistic Interpretability Glossary"]. ''Neel Nanda''.</ref> It is "the ability for the decision processes and inner workings of artificial intelligence and machine learning systems to be understood by humans or other outside observers."<ref name="lesswrong-interp" />

'''Mechanistic interpretability''' (often abbreviated as '''mech interp''', '''mechinterp''', or '''MI''') is a prominent subfield of interpretability within [https://en.wikipedia.org/wiki/Explainable_artificial_intelligence explainable artificial intelligence] and the field of study that attempts to reverse engineer neural networks from the learned weights down to human-interpretable algorithms where it's possible. It attempts to understand how neural networks perform the tasks they perform by analyzing which mechanisms are present in their computations when they are present, for example by finding interpretable [[feature|features]] and [[circuit|circuits]] in transformer models using [[Sparse autoencoder|sparse autoencoders]] and [[Attribution graph|attribution graphs]], such as how models add two numbers together.<ref name="nanda-glossary" /><ref>[https://en.wikipedia.org/wiki/Mechanistic_interpretability "Mechanistic interpretability"]. ''Wikipedia''.</ref><ref>[[On the Biology of a Large Language Model]].</ref> The approach is "analogous to reverse engineering a compiled program binary back to source code."<ref name="nanda-glossary" /> "Mechanistic" refers to the emphasis on trying to understand the actual mechanisms and algorithms that possibly compose the network.<ref name="nanda-glossary" /> "In contrast, many forms of interpretability seek to explain how the network's outputs relate high level concepts without referencing the actual functioning of the network."<ref name="nanda-glossary" /> "[[Saliency map|Saliency maps]] are a classic example,"<ref name="nanda-glossary" /> "seeking to attribute some output to a part of a specific input, such as clarifying which pixels in an input image caused a computer vision model to output the classification 'horse',"<ref name="lesswrong-interp" /> "as are 'build an interpretable model' techniques such as [[LIME]]."<ref name="nanda-glossary" />

== Contents ==

{| class="wikitable" style="width:100%;"
|-
! Category !! Description
|-
| [[:Category:Highlighted work|Highlighted work]] || Notable and influential work in AI interpretability
|-
| [[:Category:Papers|Papers]] || Papers in AI interpretability
|-
| [[:Category:Concepts|Concepts]] || Core ideas and terminology
|-
| [[:Category:Methods|Methods]] || Techniques and approaches used to interpret models
|-
| [[:Category:Architectures for interpretability|Architectures for interpretability]] || Architectures used to interpret models
|-
| [[:Category:Applications|Applications]] || Practical uses and deployments
|-
| [[:Category:Phenomena|Phenomena]] || Behaviors and properties analyzed
|-
| [[:Category:Theory|Theory]] || Theoretical foundations, mathematical and formal frameworks in AI and AI interpretability
|-
| [[:Category:AI architectures|AI architectures]] || Architectures of studied models 
|-
| [[:Category:Interpretable architectures|Interpretability architectures]] || Architectures that are designed to be more interpretable
|-
| [[:Category:Surveys|Surveys]] || Survey papers and literature reviews
|-
| [[:Category:Github codebases|Github codebases]] || Code repositories
|-
| [[:Category:People and groups|People and groups]] || Researchers, labs, and organizations 
|-
| [[:Category:Communities|Communities]] || Communities on Discord, Slack, etc.
|-
| [[:Category:Feeds|Feeds]] || Feeds for papers, blogs, newsletters, and content feeds
|-
| [[:Category:Youtube channels|Youtube channels]] || Video content and educational channels
|-
| [[:Category:Resources for learning|Resources for learning]] || Tutorials, courses, and learning materials
|-
| [[:Category:Events|Events]] || Conferences, workshops, and meetups
|}

== Pages ==

=== [[:Category:Highlighted work|Highlighted work]] ===

* [[Progress measures for grokking via mechanistic interpretability]]
* [[Towards Monosemanticity: Decomposing Language Models With Dictionary Learning]]

=== [[:Category:Papers|Papers]] ===

* [[Progress measures for grokking via mechanistic interpretability]]
* [[Towards Monosemanticity: Decomposing Language Models With Dictionary Learning]]

=== [[:Category:Concepts|Concepts]] ===

* [[Feature]]

=== [[:Category:Methods|Methods]] ===

* [[Dictionary learning]]

=== [[:Category:Architectures for interpretability|Architectures for interpretability]] ===

* [[Sparse autoencoder]]

=== [[:Category:AI architectures|AI architectures]] ===

* [[Transformer]]
* [[CNN]]

=== [[:Category:Phenomena|Phenomena]] ===

* [[Alignment]]
* [[Grokking]]

=== [[:Category:Theory|Theory]] ===

* [[A Mathematical Framework for Transformer Circuits]]
* [[The Principles of Deep Learning Theory]]
* [[Geometric Deep Learning: Grids, Groups, Graphs, Geodesics, and Gauges]]

=== [[:Category:Surveys|Surveys]] ===

* [[Mechanistic Interpretability for AI Safety -- A Review]]
* [[Locate, Steer, and Improve: A Practical Survey of Actionable Mechanistic Interpretability in Large Language Models]]
* [[An Extremely Opinionated Annotated List of My Favourite Mechanistic Interpretability Papers v2]]

=== [[:Category:Github codebases|Github codebases]] ===

* [[TransformerLens]]

=== [[:Category:People and groups|People and groups]] ===

* [[Neel Nanda]]

=== [[:Category:Communities|Communities]] ===

* [[Mech Interp discord]]

=== [[:Category:Feeds|Feeds]] ===

* [[Anthropic Interpretability research]]
* [[Transformer Circuits Thread]]

=== [[:Category:Resources for learning|Resources for learning]] ===

* [[ARENA]]
* [[How to become a mechanistic interpretability researcher]]

== Random page ==

[[Special:Random|Click here to go to a random page on the wiki!]]

== References ==

<references />

== Tips ==

* To check which pages link to the page you're on, go to the Tools menu on the top right and click on "What links here".
* To enable dark mode, log in, go to Preferences, Appearance, and select Dark. Alternatively, use the [https://chromewebstore.google.com/detail/dark-reader/eimadpbcbfnmbkopoojfekhnkhdbieeh Dark Reader] Chrome extension, but it might be a bit broken.

== Wiki created by == 

* Burny ([https://burnyverse.com/ website], [https://x.com/burny_tech X], [https://github.com/BurnyCoder GitHub], [https://www.linkedin.com/in/libor-burian-1113b0207/ LinkedIn], [https://www.facebook.com/burian.libor/ Facebook], [https://t.me/burnytech Telegram], [https://burnytech.bsky.social BlueSky], [https://mathstodon.xyz/@Burny Mastodon], Discord: burnytech, [mailto:burian.lib@gmail.com burian.lib@gmail.com]).
