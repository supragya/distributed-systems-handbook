# First few important terms
Before we begin learning PLONK, let's start with a few important terms that we will keep seeing across different ZK systems. These would be *SNARK*, *STARK*, *PCS* and *Poly-IOP*.

```mermaid
    graph TD;
        A-->B;
        A-->C;
        B-->D;
        C-->D;
```

## SNARKs and STARKs
- A *SNARK* is an abbreviation of the phrase "Succinct Non-Interactive ARgument of Knowledge"
- A *STARK* is an abbreviation of the phrase "Scalable Transparent ARgument of Knowledge"

In essence, SNARKs and STARKs are zero-knowledge proof technologies that allow one party (commonly referred to as the "prover") to prove to another "verifier" that a statement is true. These form an "argument of knowledge" or in even simpler terms, a prover provides to the verifier an "argument of knowledge" that he knows something (let's just call it some value \\(x\\)) that verifer wants to ensure that prover has.

One practical \\(x\\) could be a password which a server (the "verifier") wants to ensure a user (the "prover") has before the server authenticates user for accessing some dashboard. It's subtle, but do realize that the server doesn't want the user to give the password to it, instead it can authenticate the user as soon as such user is able to provide an undeniable "argument of knowledge" of the password in question.

Also, when we talk about "statement" in the above context, for which we want to present the "argument of knowledge", the statement could be as expressive in theory as you may want (with caveats of course). Large execution altogether, even upto the extent of correctly training an neural network maybe thought about as a "statement" and hence can be argued for. Due to this large flexibility in what we can call "statement", more often than not in our use cases, SNARK and STARK are used to argue for correct execution of some arbitrary program. You can assume this use case as the **"proof of computational integrity"**.

Anyways, back to our example prior to the above paragraph, *SNARK* and *STARK* are such "argument of knowledge" that won't provide the verifier with \\(x\\) but would provide it with an undeniable{{footnote: undeniable very often means mathematical and cryptographically backed security based argument in this context}} "argument of knowledge" of them knowing \\(x\\). We will discuss how these "arguments of knowledge" look like later, but assuming them to exist (in a sense, working black-box), we can choose the nature of "argument of knowledge" we want. If we want smaller sized arguments of knowledge in which we do not expect verifier to be online during the proof generation phase, we go with "succinct non-interactive" version of "argument of knowledge" a.k.a. *SNARK*. If instead, we want more flexibility in terms of trade-off, on average larger proof sizes and are not okay with a commonly frowned upon issue of "trusted setup" seen in *SNARK*, we go with *STARK*.

Of course this is a really crude way of understanding these terms, but they form the correct basis immediately needed for understanding the next study material in sequence. Over the course of this book, we will explore the commonalities, differences, pros and cons more in-depth.

## But wait, what is zk-SNARK and zk-STARK
Without going much in detail, you can think of *zk-* part in both zk-SNARK and zk-STARK as **additional guarantees** on top of what *SNARK* and *STARK* individually provide. The *zk-* part in essence allows you to say, "hey, here is an argument of knowledge of me knowing \\(x\\) *and now that you know this information (of my presenting an argument of knowledge of \\(x\\)), try as you may but you can't use this to get anywhere closer to finding \\(x\\) yourself*". In essence, if all the *verifier's* goal was to get the argument of knowledge and use this information to extract some additional information that may have aided him in finding \\(x\\) as compared to the situation in which he had done no interaction at all with the *prover*, the *zk-* part guarantees that all such attempts are futile and **zero information is revealed even if argument of knowledge** is provided. 

This may sound complicated, but in some use cases this is a useful property that we want. Assume our example of passwords and authentication - if for some reason, the user (the prover) is interacting with a wrong server (the verifier) and provides then with an "argument of knowledge of user's password", and such information becomes useful ever so slightly as it may for the wrong server in finding the true user's password, we may potentially have leak of some information. If however, we can argue that theoretically leaking such information is impossible in the interaction between prover and verifier, we say we are leaking nothing and hence the "argument of knowledge" provided is "zero-knowledge".

However, this is not always required. If the use case is to just "compress" some computation so that runtime is easy, we can not have a *zk-SNARK* and just have a *SNARK* and all would work out fine. More often than not in practice however, many systems have *zk-* guarantees added already and the overhead of such guarantees are not high. Hence, even when *zk-* guarantees are not needed, systems such as *zk-SNARK* and *zk-STARK* are used when non-zk versions would have sufficed.

This is important to know since very often in literature as well as internet, we focus much more on *zk-SNARK* and *zk-STARK* in discussions when the *zk-* part hardly are the core features of importance.
