## 3 extended model

### 3.1 types

Did you notice what happened with Daves proposal? Didn't the organization initially agree to
decide on a name? And ![](cat.svg) clearly isn't one.
This can be solved by a **type** system: An organization can be restricted to an underlaying structure: 
a set of types it will accepts as valid candidates denoted as $\mathcal{L}$.

A type of an element can be denoted with the colon notation. For example
$"cat\,corp": String$ states, that the candidate "cat corp" has the type String. Similarly we can say ![](cat.svg) $: Image$.


In our example Dave couldn't have proposed ![](cat.svg) if the organization had the set of types or "**language**" $\mathcal{L}_1=\lbrace String \rbrace$. However, it would be a valid candidate with the language $\mathcal{L}_2=\lbrace String, Image\rbrace$. The proposed candidate has to satisfy just one of the **alternatives** in the set in order to be valid.
Another notation form for alternatives is $\mathcal{L}_2=(String | Image)$. For a language $\mathcal{L}$ we also adopt the colon notation to state that a candidate matches *one* of the types in the typeset: $"cat\,corp":\mathcal{L}_2$ is valid.

If an organization would want to find a match composed out of a name and a logo, they could have chosen the language $\mathcal{L}_3=\lbrace (String, Image) \rbrace$. A valid candidate must to contain a String and an Image:

e.g. $("catcorp",$ ![](cat.svg) $):\mathcal{L}_3$ would be a valid.

`;

md_222 =`
Note here that the type $(String, Image)$ is a **composition** out of the type $String$ and the type $Image$, so composing types is a valid operation to produce another type. We can write composition with the dot notation: $String\cdot Image$.

Also we want to allow the star operator for a language description:
$\mathcal{L}_4 = String*$ states that the type $String$ can be composed arbitrary times:
$\mathcal{L}_4=\lbrace (), (String), (String, String), (String, String, String), ... \rbrace$

e.g. $("so", "much", "feature"):\mathcal{L}_4$ is valid.

We can now use the operations (alternative, composition, star) to describe a complex structure of our organization!

An example for a complex language is $\mathcal{L}_5=(String, ( Image | String* ) )=$"WIP Name + Logo":

"Either a name and logo-sketch, or a name and a list of requirements for the logo"

Which can be understood as the language:

$\mathcal{L}_5=\lbrace (String, Image), (String), (String,String), (String, String, Sting), ... \rbrace$

So the statement: $("Catcorp", "Black\, and\, White\, Image"): \mathcal{L}_5$ is valid.
