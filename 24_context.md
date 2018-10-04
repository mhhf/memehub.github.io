### 3.3 context
The nonterminals of a grammar can also be interpreted as a named context. This is handy for context based statements such as **contextual delegations**.

Imagine in our organization in the "WIP Name + Logo" language Alice is aware about her terrible decision making for Logos. Here she can delegate her votes only in the context of ImageCtx to Charlie. Anyone still can make proposals, but Dave has a voting weight in the context of ImageCtx of 50%. In another context (like ImageDescriptionCtx) he still only has his initial voting weight of 10%.

Also imagine that Bob thinks that at the current status, images should't be considered at all. He also likes the name "OMG Systems" so he votes 0.8 for the $"OMG\, Systems"\cdot ImageDescriptionCtx$. With this statement all candidates which can be derived out of this context by using the production of the organization will receive his vote. Note that also future coming candidates automatically receives his vote! This is called **contextual voting**.


Lets see how our voting table looks

|           | ("OMG Systems")  | ("cat corp", "Black and White Image")   | ("cat corp" ,![](cat.svg))
----------- | ---------------- | --------------------------------------- | ------------
|  Alice    | 0                | 1                                       | 0
|  Bob      | 0.8              | 0.8                                     | 0
|  Charlie  | 1                | 0                                       | 1
|  Dave     | 0                | 0                                       | 1
| **total** | $0.8*30+1*20=44$ |  $1 * 40 + 0.8 * 30 = 62$               | $1 * (10 + 40) + 20 = 70$


Our consensus candidate is therefore the last candidate.
