# What is a Smart Contract Audit - an Overview and A Look at Some Useful Tools Moving Forward

Firstly, it is reccomeded to not use the term security audit and instead use the term security review.

Spearbit havve an article discussing why we should be using this terminology. Part of the reasoning is because its not a guarantee that your code is bug free, its a review - a security focussed review. An audit implies a guarantee and potential legal feelings around what it could mean.

There is no silber bullet method of conducting a security review, but we will discuss two methods that some well-known security researchers use.


[Cyfrin Audits - What is a security Audit? How to prepare for a smart contract audit?](https://www.youtube.com/watch?v=aOqhQvWhUG0)

An intersting point to note is that ***80% of all bugs are from business implementation logic*** - meaning that the majority of bugs don't have anything to do with some weird coding error, but rather a case of misunderstanding what the project is trying to do or should be doing.

### How to get the most out of an audit/review if you're a project

1. Have clear documentation
2. robust test suits ideally inlcuding fuzz tests
3. code should be commented and readable
4. modern best practises followed
5. communication between developers and auditors - developers will always have more context
6. do an initial video walkthrough of code

## Useful Security Links

[BlockThreat - Blockchain Threat Intelligence](https://newsletter.blockthreat.io/)

[Solodit - compilation of audit reports that can be browsed](https://solodit.xyz/)

[Rekt - Attacks in Web3](https://rekt.news/)

[Week In Ethereum](https://weekinethereumnews.com/)

[Consensys Diligence Newsletter](https://consensys.io/diligence/newsletter/)

[Officier CIA](https://officercia.mirror.xyz/)



## Smart Contract Development Lifecycle Overview

1. Plan and Design
2. Develop and Test
3. Smart Contract Audit/Review & Post Deploy Planning
4. Deploy
5. Monitor and Maintain

Except, security needs to be integrated into the development process and is not just a single step at the end. You wouldn't try and build a car and wait until the very end for someone to look at it to find out is has critical failure points and therefore you need to essentially start again
.
## The Audit/Review Process

At an extremely high-level, the process involves:
1. Get context
2. Tools and Manual Review
3. Write Report

A more in-depth look at the audit/review process that involves 3 main phases:

1. Initial Review
   a) Scoping
   b) Reconnaissance
   c) Vulnerability Identification
   d) Reporting
2. Protocol Fixes
   a) Fixes Issues
   b) Retests and adds tests
3. Mitigation Review
   a) (Repeat step 1)

### Important Note Regarding the Report

**In a private audit, it is your job with the report is to do whatever it takes to make the protocol/project more secure**. You are trying to teach the protocol to be more secure, so provide as much info as you need to ensure that you can achieve this.

In competitive audits, this is slightly different since you are trying to optimise for time, finding as many high security issues as possible, there is a number of differences in the approach.

## Number 1 Tip on Improving as a Security Researcher/Reviewer/Auditor

**Repetition is the mother of skill** - The more reviews you complete, the faster and better you will develop your skills and knowledge about the process.

## Rekt Test and 

[Can you pass the Rekt test?](https://blog.trailofbits.com/2023/08/14/can-you-pass-the-rekt-test/)

"The Rekt Test focuses on the simplest, most universally applicable security controls to help teams assess security posture and measure progress"


[nascentxyz/simple-security-toolkit](https://github.com/nascentxyz/simple-security-toolkit/blob/main/pre-launch-security-checklist.md)

There are a few checklists here that are different takes on the idea of teh Rekt test. Both are great and can be used in conjunction with each other.

## Can tools replace a human reviewer?

[Demystifying the Explotable Bugs in Smart Contracts](https://github.com/ZhangZhuoSJTU/Web3Bugs/blob/main/papers/icse23.pdf)

In this paper, the authors explored what bugs that have been found in the real world could have been found with tools. What they found is that around 80% of bugs reported were 'machine unauditable', meaning that 80% of the bugs were only found because of security personnel! And this aligns with the statement made earlier that the majority of bugs reported were due to business implementation logic issues.

## Top Web3 Attacks

Here is a list of the top 10 attack vectors used causing hundreds of millions of dollars of loss (2023):

1. Stolen Private keys
2. Reward Manipulation
3. Price Oracle Manipulation
4. Misonfiguration
5. Insufficient Function Access Control
6. Logic Error
7. Function Paramter Validation
8. Read-Only Reentrancy
9. Reentrancy
10. Governance

