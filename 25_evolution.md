### 3.4 evolutions

In the previous examples the organization started with the Grammar "Name" and **evolved** into an organization of the type "WIP Name + Logo". It made this transition by changing the grammar and by porting *some* of the candidates and possibly making other adjustments.

We can define an Evolution formally by a mapping from one organizational state to another:
$$evolution := O_{G_1} \rightarrow O_{G_2}$$

This takes a grammar which the organization is defined in ($G_1$) and maps or filters all of its candidates to candidates which are valid in the grammar $G_2$. It can also make other changes like minting new shares and giving them to the actor, who proposed the winning candidate or change votes and delegations. After the change, it takes the new grammar $G_2$ as its new foundation.

Evolutions are a powerful tool and therefore are only applied when their votes hit a $\frac{2}{3}$ majority.

The set of all defined grammars and evolution-schemas can be seen as a global knowledge base and a path from the current grammar representation to a desired as a "blueprint" or a "recipe" to arrive at the desired goal by following a step by step guide.

<center> ![](ev.svg) </center>

