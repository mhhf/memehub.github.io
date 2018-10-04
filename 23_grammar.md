### 3.2 regular grammar
In theoretical computer science a description schema to produce a language is a grammar, in our case a regular grammar.

A regular grammar is a composition out of the rules: concatenation, alternative and Kleene.
Formally it is:
* set of terminals $T$ (types: e.g. String, Image, Boolean, Number, ...)
* set of nonterminals $N$ (Contexts - such as \"UI\", \"NameContext\", etc. )
* start rule $S$, which has to be a Nonterminal (e.g. \"Start\")
* set of production rules in one of the following forms: $P \rightarrow t P'$, $P \rightarrow t$ or $P \rightarrow \varepsilon$ ($\varepsilon$ is the empty production)

The \"WIP Name + Logo\" language looks like following in a grammar description $G$:

<p class="eq">
  $T = \lbrace String, Image \rbrace$
  $N = \lbrace Start, ImageCtx, ImageDescriptionCtx \rbrace$
  $S = Start$
  $P = \lbrace$
  $  Start \rightarrow String \cdot ImageCtx, $
  $  Start \rightarrow String\cdot ImageDescriptionCtx, $
  $  ImageCtx \rightarrow Image, $
  $  ImageDescriptionCtx \rightarrow String \cdot ImageDescriptionCtx, $
  $  ImageDescriptionCtx \rightarrow \varepsilon $
  $ \rbrace$
</p>

The grammar is a way to describe the language, by starting with the Start rule and following the production rules untill the end. With this one can proof or disproof the validity of a candidate.

For example the type: $(String\cdot String)$ can be prooven via:

<p class="eq">
  $Start$ 

  $\rightarrow String\cdot ImageDescriptionCtx $

  $\rightarrow String\cdot String\cdot ImageDescriptionCtx $

  $\rightarrow String\cdot String $
</p>

This is also a **proof** for the candidate: $"Catcorp" \cdot "Black\, and\, White\, Image"$.

We can restrict an organization to a grammar: $O_G$ which will handle the candidate validation.
