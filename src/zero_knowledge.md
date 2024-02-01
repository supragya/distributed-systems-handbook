# Onto the world of zero knowledge
We begin our journey into mystical lands of zero-knowledge when talking about distributed systems, especially ones pertaining to blockchains. Why? Quite simply because going forward we are going to see many projects in the ecosystem embracing this technology. You may quickly begin asking yourself why again! What does ZK (commonly used abbreviation for "zero-knowledge") provide that is so lucrative that many projects are trying to embrace it?

In very crude terms, very often zero-knowledge helps you "offload computation outside the system trustlessly". Let's try to break it down.

> "offload computation outside the system"

Remember, why struggle with different "consensus" mechanisms such as BFT etc shearly because we want an agreement between parties on what happened and what didn't happen. Sometimes its purely opinions, such as "while we both think transaction \\(T_A\\) and \\(T_B\\) are correct, I want \\(T_A\\) to happen sequentially prior to \\(T_B\\)" while sometimes it's about the integrity of the systems, such as "transaction \\(T_A\\) is incorrect and should not be included".
