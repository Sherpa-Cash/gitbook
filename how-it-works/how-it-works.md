# How It Works

Transactions in a blockchain ultimately form one long chain, which makes it easy to trace. Sherpa Cash improves transaction privacy by breaking the on-chain link between the recipient and destination addresses.

It does this using a smart contract that accepts deposits for a certain token at a fixed denomination. For example, the 0.1 AVAX contract will only allow deposit and withdrawal of 0.1 AVAX. At launch we will have the following token and denomination combos available:

* 0.1 AVAX
* 1 AVAX
* 10 AVAX
* 100 AVAX

Once the funds are deposited, the user will receive a "note", which is proof or claim to your deposited funds. This note is then used by another address to withdraw the same amount of funds that you deposited. As a result, you will have transferred funds from one address to another address without there being a direct link between the two addresses. 

This all sounds very confusing, so allow us to explain with a simple example. Imagine Alice wishes to transfer 100 AVAX from wallet A to wallet B:

1. Alice first deposits 100 AVAX into the 100 AVAX Sherpa contract. In return, she receives a note that looks something like below. **This note must be kept secret!** 
2. To withdraw the 100 AVAX, Alice simply pastes in the note and her wallet B address and calls the withdraw function. And voila, that's it!

```text
sherpa-eth-0.1-1-0x07f00caa131a209ac0db1401be7f2f568d8a49f0459e92a5b9e28610ac71fad948537e978ece8a62091b9305a8df2817113f7e8010c5ec5510149c5bfb25
```

### **Withdrawing via Relayer**

* The issue with withdrawing is that it requires gas. Gas is essentially AVAX that came from somewhere, i.e. it is traceable. What if Alice wants to withdraw to an address with a fresh transaction history?
*  In that case, she can withdraw via a relayer. The relayer simply calls the withdraw function for her and then transfers the funds to her wallet with the gas fee deducted.

### **Anonymity Set**

* The anonymity set is the number of deposits your withdrawal could potentially originate from. 
* If the anonymity set is 1, then the withdrawal will inexplicably be linked to your deposit. 
* So the higher the number, the harder it is for your withdrawal to be linked to your deposit.
* Because of this, we often advise to wait a bit for the anonymity set to increase before withdrawing.

### Sounds like magic, but how does it do this?

The secret sauce is all in the **note** that is generated when you deposit. Upon presenting the contract with your note, it first checks that your deposit was made, then it checks that you haven't spent your withdrawal already. How it does this is through zero-knowledge cryptography which is detailed in the original whitepaper. Once both checks pass, the contract then allows you to withdraw your funds.



