## 4. Implementation

### 4.1 data structures
To save space due to the linear structure of regular grammars, we can save all
valid candidates, contextual votes and delevations in a prefix tree:
<center> ![](trie.png) </center>

The tree is a compact representation, holding all nessecery information.

Votes and delegations are inhereted to a "leaf" node where the transitive hull of delegations is computed.
Its acting on the vote matrix complements the vote matrix ("add the delegated votes to the vote matrix for each actor which hasn't voted for himself").
Now the known consensus function is used to compute the consensus candidate out of the leaf nodes.


### 4.2 architecture

The main part of an organisation is a contract on the ethereum blockchain described in 3.2.1. Users interact
with the contract either through a command line interface or a graphical user interface described in 3.2.2.

### 4.2.1 On chain
The current solidity contract can be found on [github.com](https://github.com/mhhf/mem/blob/develop/src/contracts/sol/org.sol). The code is under active development and in an experimental stage.


<center> ![](actions.svg) </center>

The core part of an organization is implemented on the Ethereum blockchain. A user can
iteract with it by either:
* **createOrg** creating a new organization
* **send**: sending shares from the own account to another actor
* **propose**: propose a new candidate
* **vote**: vote for an existing candidate
* **delegate**: delegate his votes to another actor in a particular context
* **getConsens**: ask for the current consens
* **voteEvolution**: vote on a evolution step for the organization

##### 4.2.1.1 createOrg
this creates a new organization

parameters:
* bytes language: is a regular grammer
* uint shares: initial size of the organization

#### 4.2.1.2 send

sends shares from the own account to a given actor.

parameters:
* address to: the address of the actor who should receive the shares
* uint value: the amount of shares to send

#### 4.2.1.3 propose

propose a new candidate

parameters:
* bytes data: serialized candidate data and context description
* bytes type: serialized type description

#### 4.2.1.4 vote

votes for a node in a prefix trie

parameters:
* bytes32 nodeId: the id of the node
* uint value: the rating of the node (0 - 1000)

#### 4.2.1.5 delegate

delegates the vote to another actor for a given context

parameters:
* address to: the address of the delegate
* bytes32 nodeId: the context - a node in the prefix trie

#### 4.2.1.6 getConsens

returns a leaf node id which can be used to resolve the actual type and data of the consens candidate

#### 4.2.1.7 voteEvolution

vote for an evolution for this organization, if its not proposed, propose it first

parameters:
* bytes32 evolutionId: the id of the evolution
* uint value: the rating of the evolution (0 - 1000)


### 4.2.2 Off chain

Currently the off chain implementation is under active development and not in a working stage.
The current experimental implementation can be found [here](https://github.com/mhhf/mem/tree/develop).

#### 4.2.2.1 CLI - command line interface

Here we show an example interaction with the contract over a command line interface for the example shown in section 2.1:

First the organization itself has to be created by one of the owners.
Alice could do something like this:
```sh
> mem new startup --share 10000 --lang=short_simple_name
```

this creates an organzation with a temporary reference *startup*, alice 
receives an initial amount of *10000* shares and the language of this org is
*short_simple_name* which is a reference to another org which decides on what a name should be,
lets see what they've decided upon:
```sh
> mem get short_simple_name
{ type: 'string', pattern: '^[a-z ]{3,32}$' }
```
Here it is a string between 3 and 32 characters which contains letters from a-z and a blank character.

After the org is created alice wants to add its other owners, by transferring them
their initial shares:

```sh
> mem send startup <bob> 3000
> mem send startup <charlie> 2000
> mem send startup <dave> 1000
```

Note that *< bob >, < charlie >, < dave >* are references for addresses of the actors.

This creates our initial ownership distribution.

Now every owner is able to do proposals as long as they are valid words of the language.

**proposals**

Alice propose *Awesomecorp*:
```sh
> mem propose startup -s "Awesomecorp"
```

Bob proposes *omg systems*:
```sh
> mem propose startup -s "omg systems"
```

And Dave tries to propose <cat.png> but fails because it is rejected by the language.
```sh
> mem propose startup ./cat.png
```

**voting**

Now everybody votes( this shows only the case of Alice ):

```sh
> mem vote startup "Awesomecorp" 1
> mem vote startup "omg systems" 0.3
```

**consensus**

Great. now after everybody voted on the candidates, we can see what the consensus
of the decision was:

```sh
> mem get startup
OMG systems
```

**evolution**

Now the organisation want to evolve: Fist we search for possible next evolution steps.
Then we see which evolution is already proposed:
```sh
> mem evolution next startup
  name_to_wip_name_and_logo     - Helps you to find a logo for your organisation, keeps only the consensus name
  name_to_simple_landing_page   - A simple landing page provided do display provided features, keeps all names
  business_model_canvas - Helps you to find a business model for your organisation, removes all names

> mem evolution get startup
  name_to_wip_name_and_logo - 60%
```

Great, we want to find a logo next. Therefore we also vote for the evolution wip_name_and_logo

```sh
> mem evolution vote startup name_to_wip_name_and_logo 1000
```

This will trigger evolution as the new votes hit > 66% and the new grammar of startup becomes wip_name_and_logo with a single candidate - "OMG systems"

#### 4.2.2.1 GUI - graphical user interface

The GUI is not implemented yet, but its major components already defined. Here we will give an overview over them:

Requirements for an first abstraction layer:
1. easy creation of languages
2. propose candidates
3. list, view, preview a candidate
4. vote for a candidate
5. delegate votes
6. send shares
7. view the current consensus candidate
8. vote for evolutions
9. easy creation of evolutions

For the creation of a regular languages first we will take a subset of [JSON-schema](json-schema.org).
JSON-schema is an easy readable and established standard for json type definition. A subset of Json-schemas, namely those which don't contain recursive references, can be taken to produce a regular grammars. We will take this subset to produce arbitrary languages for organizations.

Json Schemas are mainly used to validate json objects and to generate forms to view and manipulate valid objects. Therefore Json-Schemas are a great tool to use to satisfy the requirements 1, 2, 3, 4, 5, 7.
To achieve even more simplicity for writing json schemas a form builder can be introduced such as [this](https://github.com/Kinto/formbuilder) or one of many others.
In section 7. is a demo of a Json-Schema, which produces an editable form and a regular grammar.
For the tasks 6. and 8. custom GUI elements will be engineered.
Evolution schemas (9.) will be created as solidity contracts, since they require complex operations, such as mapping and filtering the candidates and manipulating votes and delegations.
