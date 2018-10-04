#### 2.2 consensus
We can calculate the actual outcome by considering the votes for each candidate
together with the shares of each voter:

<div id="chart"></div>

The winner candidate is "omg systems" with 2 shares ahead of "Awesomecorp".

Note here that its possible for two candidates to receive the same maximal value.
(For example if charlie had voted 0.1 with 20 shares which would put "Awesomecorp" to 52 shares total.)
In this case we need a system to decide which candidate actually has won: Since
"Awesomecorp" was proposed before "omg systems", we simply will take the oldest candidate with the maximum value:
Mathematically speaking we need a strict total order over the candidates:

$$<\subset K\times K$$

This approach gives us a **consensus** function, which is deterministic on every organization state:

$$consens(O):= min_<(\lbrace k\ |\ value(k) = \max_{k'\in K}(value(k'))\rbrace )$$
$$value(k):=\sum_{a\in A} share(a)*vote(a,k)$$

### delegations

In order to make voting more efficient we can bring in the concept of transitive voting (or delegation).
Suppose in our scenario Dave don't really have the time to evaluate all candidates in this difficult decisions. He also trusts his fried Bob to represent his interest, so he decides to delegate his vote to Bob. Now, every time bob votes or delegates, Daves votes will be taken in to account.

<center> ![](D.svg) </center>

Mathematically we define a delegation set:
$$D \subseteq A\times A$$

And in our example Dave is delegating to Bob:
$$D=\lbrace  (Dave, Bob) \rbrace $$


When we look again at our vote matrix, the result would look like this:

|           | Awesomecorp   | omg systems   | ![](cat.svg)
----------- | ------------- | ------------- | ------------
|  Alice    | 1             | 0.4           | 0
|  Bob      | **0**         | **1**         | **0**
|  Charlie  | 0             | 0             | 1
|  Dave     | **0**         | **1**         | **0**

In this example his delegation actually didn't change the outcome but did had an effect
on the overall rating of the candidates: Awesomecorp is rated with 40 shares and
omg systems with 56 and ![](cat.svg) with 20.
