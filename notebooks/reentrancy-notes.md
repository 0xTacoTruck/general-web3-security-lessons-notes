## Reentrancy

Reentrancy attacks are when a function is called and due to some external call the protocol tries to make, an attacker can re-enter into the same function - or call some other functions or read some state, and then re-enter into that function.

https://github.com/pcaversaccio/reentrancy-attacks -> This repository contains a list of reentrancy attacks and different types of reentrancy attacks that have occurred.

The situation tends to arise when the CEI (checks, Effects on self, Interactions with other contracts) design principles are not followed.

The easiest scenario to understand reentrancy is when a smart contract attempts to transfer the amount of ETH the user has deposited to the contract back to the user in a withdraw-like function and the address it tries to send the ETH to is a smart contract that has been maliciously designed so that upon receiving ETH it immediately calls the withdraw function again because the protocol has not had a chance to update the balance to zero for that address yet.

![Reentrancy Demo](img/reentrancy-demo-diagram-combined.png)

Some reentrancy attacks may use the receive function to call other functions prior to reentering into the original function if that can lead to a gaining of advantage for an attacker.

### Reentrancy Attack Vectors

**Direct External Calls:** Smart contracts often interact with other contracts or external entities through external function calls. An attacker can create a contract with a fallback function that calls back into the vulnerable contract before the initial function call completes. This can lead to unexpected behavior, allowing the attacker to manipulate the vulnerable contract's state.

**Fallback/Receive Function:** Solidity contracts include fallback and/or receive function that is invoked when a contract receives Ether without any data or when a function call fails. If this fallback and/or recieve function involves interaction with external contracts before completing its execution, it can be exploited by attackers to create reentrancy vulnerabilities.

**Cross-Function Reentrancy:** Even within a single contract, reentrancy vulnerabilities can arise if multiple functions within the contract interact with each other and external contracts in such a way that the state is not properly managed between function calls. This can create opportunities for an attacker to repeatedly call functions before previous calls are fully processed.

**External Calls Within Loops:** Loops in smart contracts can be particularly vulnerable to reentrancy attacks if they contain external calls. If the loop is not properly controlled or if the state changes as a result of an external call within the loop, an attacker may be able to repeatedly invoke the loop, exploiting the vulnerable state of the contract

### Quick Attacker Mindset Questions for Reentrancy Attack Vectors

- What external calls is the contract making?
- Is the contract relying on use of another function to calculate something in this function? Can I call that function prior to finishing this one to break the expected values this function needs?
- What interval of value amounts can I use to steal funds without causing a revert?
- Can I call a known function that this target function uses in order to manipualte something in this function?
- Can I trigger a broader system event by receiving something and immediately calling an unprotected external function before this completes?
- The mroe complex a system, the harder it will be for them to control and prevent reentrancy attacks - have they missed something in the complexity?
