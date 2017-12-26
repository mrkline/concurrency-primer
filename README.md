# What every systems programmer should know about concurrency

This repo contains the LaTeX source for a pretentiously-named,
but hopefully concise,
introduction to low-level concurrency.

## Where do I get a copy?

The latest version should always be available at
<http://assets.bitbashing.io/papers/concurrency-primer.pdf>.
You can also find a rendered PDF for each tag with its release notes on
[Github](https://github.com/mrkline/concurrency-primer/releases)
and [Gitlab](https://gitlab.com/mrkline/concurrency-primer/tags).

## How do I build it?

1. Install a modern, Unicode-aware LaTeX, such as LuaLaTeX.
   On Linux, this is usually as simple as installing your distro's TeX Live
   package, e.g., `texlive-base` or `texlive-core`.
   The same package should also provide the `latexmk` script.
   (See below)

2. Install [pygments](http://pygments.org/), a Python syntax highlighter.
   This is used by the LaTeX package [minted](https://ctan.org/tex-archive/macros/latex/contrib/minted/)
   to handle our syntax highlighting.

3. Change the fonts as-needed.

   The official version is typeset with Matthew Butterick's
   [Equity](https://typographyforlawyers.com/equity.html),
   Christian Schwartz's [Neue Haas Grotesk](http://www.fontbureau.com/NHG),
   and [mononoki](https://madmalik.github.io/mononoki/) by Matthias Tellen.
   In the likely case that you don't have all of these on your system,
   you'll need to change the [fontspec](https://ctan.org/pkg/fontspec)
   declarations near the top of the `.tex` file.
   (You might want to tweak or remove the
   [colophon](https://en.wikipedia.org/wiki/Colophon_(publishing))
   while you're at it.)
   You can also change the body font size by changing
   `\documentclass[fontsize=10pt, ...`
   to whatever you prefer.

4. Build the document using

       latexmk -lualatex -latexoption=-halt-on-error -latexoption=-shell-escape concurrency-primer.tex

   Note that `latexmk` will run LuaLaTeX multiple times, since
   TeX generates cross references in one pass, then links them in a second.

   If you can't use `latexmk` for some reason, you can manually invoke

       lualatex -halt-on-error -shell-escape concurrency-primer.tex

   until it no longer warns,
   "Label(s) may have changed. Rerun to get cross-references right."

5. Enjoy a beautifully typeset concurrency-primer.pdf.
