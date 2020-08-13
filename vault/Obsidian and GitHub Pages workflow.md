For easy sharing and viewing on mobile, I publish my [[Obsidian]] vault to <http://www.kmaasrud.com/brain/>. To make the note-taking process as simple and frictionless as possible, I've set up automated publishing using [[Hugo]] and [GitHub Pages](GitHub Pages.md) (as well as a [[Python]] script I've written myself). This is whats needed to get it set up:

## Some sort of [[Version control system|VCS]]
I use [[Git]] as my preffered [[Version control system|VCS]] and host my vault on [[GitHub]]. Using version control, I'm able to track how my notes evolve over time and roll back changes if necessary. This is in contrast to automatically syncing to the cloud with a service like [[OneDrive]] or [[Dropbox]]. Hosting my vault on [[GitHub]] also allows me to use [[GitHub Actions]] to easily automate the following actions.

## Convert propietary [[Obsidian|Obsidian]] syntax into [[Hugo]]'s [[CommonMark]] compliance
Even though I'm able to only use vanilla [[Markdown]] syntax in [[Obsidian|Obsidian]] and achieve much the same result - the [[Wiki-style links|wiki link syntax]] is a lot quicker and intuitive for me. Thus, I need them converted into complying with [[Hugo]] and how it handles relative links. I do this using a [Python script](https://github.com/kmaasrud/obsidian-hugo) I've written. Here's a list of what needs to be replaced:

- `[[wiki link]]` -> `[wiki link]({{< ref "wiki link.md" >}})`
- `[[wiki links|alias]]` -> `[alias]({{< ref "wiki link.md" >}})`
- `[[wiki link#header name]]` -> `[wiki link]({{< ref "wiki link.md#header-name" >}})`
- `![[image or embed]]` -> `![](image or embed)` (NOTE: Embedding other [[Markdown]] files is not part of [[CommonMark]] and must therefore be replaced by a link)

## Making a static site using [[Hugo]]
With the content properly formatted, [[Hugo]] does the heavy lifting. For [[GitHub]] users like myself, there's a great [[GitHub Actions|Action]] found [here](https://github.com/peaceiris/actions-hugo) that has [[Hugo]] generate the site and later pushes the generated content to another repo or branch. This is perfect, as it allows me to have the source of my site separated from the content that is published through [[GitHub Pages]].

## Publishing everything through [[GitHub Pages]]