# The first ZK system: PLONK

In our quest to begin understanding zero-knowledge systems, we need to pick a system and get our hands dirty. We pick PLONK{{footnote: [Original PLONK paper](https://eprint.iacr.org/2019/953.pdf)}} as our first zero-knowledge system. This is shearly because of following reasons:
1. **Popular base system**: PLONK is a popular zero-knowledge system that forms as a good zk system itself as well as the base foundational system for many other ZK systems like PLOOKUP, HyperPLONK, TurboPLONK, PLONKY2 etc.
2. **Relatively higher amount of resources**: As a first ZK system to learn, PLONK resources are much more available over the internet which both tackle it theoretically and practically.

## Understanding the first few important terms
Before we begin learning PLONK, let's start with a few important terms that we will keep seeing across different ZK systems. These would be *SNARK*, *STARK*, *PCS* and *Polynomial IOP*.
- A *SNARK* is an abbreviation of the phrase "Succinct Non-Interactive Argument of Knowledge"
- A *STARK* is an abbreviation of the phrase "Scalable Transparent Argument of Knowledge"

In essence, SNARKs and STARKs are zero-knowledge proof technologies that allow one party (commonly referred to as the "prover") to prove to another "verifier" that a statement is true. These form an "argument of knowledge" or in even simpler terms, a prover provides to the verifier an "argument of knowledge" that he knows something (let's just call it some value \\(x\\)) that verifer wants to ensure that prover has.

One practical \\(x\\) could be a password which a server (the "verifier") wants to ensure a user (the "prover") has before the server authenticates user for accessing let's say some dashboard. It's subtle, but do realize that the server doesn't want the user to give the password to it, instead it can authenticate the user as soon as such user is able to provide an undeniable "argument of knowledge" of the password in question.

*SNARK* and *STARK* are such "argument of knowledge" that won't provide the verifier with \\(x\\) but would provide it with an undeniable "argument of knowledge" of them knowing \\(x\\). We will discuss how these "arguments of knowledge" look like later, but assuming them to exist (in a sense, working black-box), we can choose the nature of "argument of knowledge" we want. If we want smaller sized arguments of knowledge in which we do not expect verifier to be online during the proof generation phase, we go with "succinct non-interactive" version of "argument of knowledge" a.k.a. *SNARK*. If instead, we want  
