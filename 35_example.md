## 5 Example
A real world example is the recent [discussion about a standard coin contract interface](https://github.com/ethereum/EIPs/issues/20). The discussion was held on different platforms in an unstructured way and therefore it took a long time for the community to form a consensus. Now other contract interface standardization discussions are held for verity other domains following the same unstructured process. The following is an example how a interface standardization could be implemented on top of the presented model.


An organization can be formed around a specific api standardization task, in our case the coin/ tokens. They pick a grammar, which describes the application binary interface and the natspec documentation of every interface point.
The language could looks like this:

```sh
standardABI:=(Interface Natspec)*
Interface:= FunctionName FunctionParameter* ReturnParameter*
FunctionName := string
FunctionParameter := Type Name
ReturnParameter := Type Name
Type := string
Name := string
NatSpec := String
```

With this a structural discussion is possible. Candidates can be submitted in a clear fashion. Contexts like documentation can be delegated. The clear distribution of votes and shares makes the decision process transparent. Every program can link against this organization to use the consensus candidate **before** the organization agreed on a final consensus. The generation of common interpretations makes the candidate always reviewable and easy to work with, regardless of the specific standardization task:

<center> ![](abi.svg) </center>

