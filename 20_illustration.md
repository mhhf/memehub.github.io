## 2 general model

#### 2.1 organization

Suppose there is organization $O$ with is owned by Alice, Bob, Charlie and Dave
who have agreed to find a name for it. This problem is kind of trivial, but we
want to study it in depth to lay out the mathematical foundations behind it.

<center> ![](A.svg) </center>

Every person, who has impact on this decision is member of a set of **owners**
mathematically represented as a set $A$:

$$A = \lbrace Alice, Bob, Charlie, Dave \rbrace$$

The influence of each Member on this decision don't has to be equal. Suppose
there are 100 shares in total. The ownership of **shares** represents
the influence each owner has on the outcome. We can define a share function
which assigns each owner the number of shares he own.

$$share: A \rightarrow \mathbb{N}$$

The sum of all shares is called the **size** of this organization:
$$|O|: = \sum_{a \in A} share(a)$$

In our example Alice has 40 shares which represents 40%, Bob 30, Charlie 20 and Dave 10.

<div id="chart1"></div>

Now everybody can propose a name:

<center> ![](K.svg) </center>

We can call all proposals - **candidates**. Our final candidate set looks like the following:
<center class="oneline">
$K=\lbrace "Awesomecorp", "omg\, systems",$ ![](cat.svg) $\rbrace$
</center>


Now every owner can rate each candidate:

|           | Awesomecorp   | omg systems   | ![](cat.svg)
----------- | ------------- | ------------- | ------------
|  Alice    | 1             | 0.4           | 0
|  Bob      | 0             | 1             | 0
|  Charlie  | 0             | 0             | 1
|  Dave     | 1             | 1             | 1


The evaluation of the candidates by the owners can be represented by a **vote** function:
$$vote: A\times K \rightarrow [0,1]$$

The organization now contains all information we need, to determine the actual winner:

We define an organization state as a tuple:
$$O:=(A,K,<,share,vote)$$
