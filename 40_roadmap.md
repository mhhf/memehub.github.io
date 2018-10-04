## 6. Roadmap

This project is still in experimental stage. But all critical parts are already implemented. The roadmap is intended to give an list over required tasks for a publicly usable version. Those tasks are split in engineering tasks for which a clear description is given and conceptual tasks which are open in their nature.

### engineering tasks
#### GUI and CLI (3 weeks for usable prototype client)

* implementation
* documentation

#### evolutions (2 weeks for prototype)

* implementation
* documentation

#### interpretations (2 weeks for prototype)

* documentation
* easy to use api
* examples

#### tests and documentation (2. weeks for prototype)

* reach a test coverage of 100%
* document the code
* easy to follow tutorial for cli/ gui covering every possible action
* easy and complex examples

#### initial deploy

For an initial set of languages online schema databases such as [schema.org](http://schema.org/) can be crawled and imported.

### conceptual tasks

#### extendability (1 weeks - ? for basic implementation)

* delegational programming
  * votes don't have to be delegated to a human actor, but can be delegated to an external contract, oracle or organization. Think about a contract which A-B tests the top rated consensus candidates and adjusts is own votes for them, basing on the results.
* in order to be able to adapt fast to future coming requirements, this system has to be as modular as possible. Therefore some time has to be spend in researching a modular architecture.

#### GUI for meta tasks

* structural discussion for organizations
  * in order to be practical a governance schema has to provide a easy method to exchange meta information such as discussion about candidates, or evolutions, search, etc.

#### scalability

* practically the actions done on ethereum are not well scalable. Here time needs to be comited to explore possible scaling possibilities. Possible solutions could include:
  * sidechain
  * merkle trie challenge/ proof mechanism

#### incentivation mechanisms

* incentivation mechanisms such as rewarding actors for good proposals or penalize actors for inaction could provide an huge increase in value gain for organizations and therefore promote progress.

#### MLCFG

The presented concept is not only valid for regular grammars, but as well for metalinear contextfree grammers, which increases the expressibility. Exact implications are a open study subject.

#### other enhancements

* anonyme voting
* prevention of strategic voting through commitment based voting
