## 1. Abstract
> Imagine if you could not only vote for reddit posts, but govern the entire platform with your interactions.

With the emergence of decentral organizations such as Bitcoin, Ethereum or Applications written on top of Ethereum new forms of governance are needed to direct and evolve this organizations. Such schemas need to be transparent, fair (influence is directly proportional to the ownership), accessible (easy to interact with), extendable, proposed candidates have to be previewable, and verifiable and decissions have to be automatically enforcible. Currently this is still an unsolved problem. In this paper, we analyze the problem space and propose a schema which could serve as a building block in the roadmap to a full self-governance solution.


In the presented method, governance is understood as the task for a group of **actors** (**organization**) with a clear **ownership** distribution to deterministically find a **consensus** out of a set of possible
**candidates**.

Efficient governance tries to optimize the amount of necessary interaction done by each actor to arrive at his desired and reachable state.

The main idea is the tightly coupled relationship of user interactions such as voting and delegations statements with a meta data structure.

The paper is structured in the following way: first we introduce the problem space and a general model for governance in 2. Based on this we introduce an extended model in 3. and discuss the role of data structures for governance, in particular those, which can be described with a regular grammar. In section 4 we present our current proof of concept implementation. In 5. an real world use case is given which illustrates the key value proposition of the presended model. In 4. we present the roadmap for further iterations.
