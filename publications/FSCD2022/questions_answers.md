# Info
This file contains some questions that were asked to Daniele Nantes when she
presented our paper on FSCD 2022 and our answers. 

# Questions and Answers
**Question 1** - How different was the formalized proof from the pen-and-paper proof
given that we had to use "nice inputs" to prove soundness and completeness? Were the
pen-and-paper proof correct? Did they consider nice inputs?

**Answer 1** - Stickel and Fages did not consider "nice inputs" exactly, but the use
of "nice inputs" did not represent a big deviation from the papers of Stickel and
Fages since it was relatively easy to verify that the desirable properties between $P$,
$\sigma$, $V$ hold between the recursive calls. 

The only significant error was the proof of termination given by Stickel, which
Fages discovered and fixed. But there were omissions in the paper
that we had to fill. The proof of termination suffered slight changes from Fages
paper mainly due to the fact that we avoided mutual recursion and he didn't. 
Regarding completeness, Fages just sketches the proof (pointing to the variable
abstraction principle) and Stickel gives a proof, but we were not able to fill the
omissions of Stickel's proof of completeness without first adding the hypothesis
$\delta \subseteq V$ and then proving that it can be removed (via the concept of
inputs that differ only by a renaming). Although termination and completeness were
the two hardest parts, in my opinion there were more omissions in the proof of
completeness. 

**Question 2** - How many lines of code did you have?

**Answer 2** - Before we removed the hypothesis $\delta \subseteq
V$, the .pvs files had 7226 lines while the .prf files had 341268 lines. 
After we removed this hypothesis the .pvs files have 7906 lines  and the .prf
files have 386563 lines. 

PS: Table 3 of our paper is before we removed the hypothesis $\delta \subseteq
V$. 
 
**Question 3** - Have you tried to formalise ACU-unification?

**Answer 3** - AC unification with Unit (ACU-unification) is sometimes called
AC1-unification. In our paper we briefly talked about it in Remark 10. We have not
tried to formalise ACU-unification but we imagine that our formalisation could be
adapted for the task. In terms of the functions described in Section 3.2.1, we
imagine that the main modification would be that we would no longer need function
`ExtractSubmatrices`, instead we would work only with diophantine matrix $D$. Dealing
with a equation like $f(X1, X2) =? a$ would be trickier, since we may instantiate X1
to 1 and X2 with a for instance. 

**Question 4** - Have you tried to formalise "Syntactic AC-unification" by Alexandre
Boudet and Evelyne Contejean? Perhaps it will help with nominal AC-unification. 

**Answer 4** - Thank you for the tip, we were not aware of this paper. I took a quick look and
it appears closely related to our work. When choosing the algorithm to formalise, we
were looking for a simple, classic algorithm and we were not too worried about
efficiency and that's why we chose Stickel's algorithm. The paper sounds interesting
and we will take a more detailed look to see if/how we can adapt some ideas to nominal AC-unification. 

**Question 5** - Is it possible to encode mutual recursion in PVS. Did you try to use
it?

**Answer 5** - We did not try to use it, but thought about it. 
According to page 11 of the manual: 
> "Thus, mutual recursion is not directly supported. The effect can be achieved with a
> single recursive function that has an argument that serves as a switch for
> selecting between two or more subexpressions."

When we made the decision to not use mutual recursion, we imagined that the effort to
emulate mutual recursion this way would be roughly the same than the approach we
eventualy took. We imagined that emulating a mutually recursive algorithm in PVS would, 
just like our approach, deviate slightly from the proofs in Fages paper.  In the end
we imagined that our approach would be slightly clearer to read and decided not to
emulate mutual recursion. 
