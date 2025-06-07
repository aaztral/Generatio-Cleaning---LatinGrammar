# Generation-Cleaning---LatinGrammar
Solution for the 2nd Evidence of the TC2037 Course at ITESM. Generation and Cleaning of Grammar. Armando Fuentes Silva - A01712074

## Latin
Latin is defined as a classical language, it's an italic branch of the indo-european languages, it was spoken by Latins in Latium, and the lower area of Rome. It's considered to be the influence of many languages, including the English language. 

## Latin structure and word order
Latin has a lot of freedom within the structure of a sentence, basically you can rearange the sentence without losing meaning, even when we have two nouns, for example in the english language we would find trouble if we rearange the order of a sentence with two nouns, word order determines which one is the direct object, example:

***"the dog chases the cat"***

In this sentence the dog is the one chasing the cat, if we flip the nouns it also flips the meaning. But in Latin we dont have this problem, this is because the in Latin the ending of the word changes based on it's grammar, let's check another example, now in latin:

The word ***"servus"*** is nominative, due to the ***"us"*** ending, so if we want to change it to, let's say, accusative case we would switch the ending for a ***"um"***. So in the sentence:

***"servus dominam salutat" (The slave greets the mistress)***

We can see that the slave is the one greeting the mistress. And this is always the case, no matter how we re-arrange the words, all due to the Latin Grammar. Well, this is great flexibility, but most certainly, a lot of caos, fortunatly for us (specially for me) Romans loved order, so they did had a strandard word order. 

The word order is what we call **SOV**, stands for Subject-Object-Verb.

## Grammar
Grammar in just the most global definition possible is thw whole system and structure of a language, basically how its structured a grammar includes a set of rules from which we can derive strings. These rules are statements of logical equivalence of the form: ψ → ω, where ψ and ω are strings.

The example given in my lecture was the following: 

Here is a very simple example of a grammar to generate the string "the dog saw a man in the park"

    S -> NP VP
    NP -> Det N | Det N PP
    PP -> P NP
    VP -> V NP | VP PP
    Det -> 'the' | 'a'
    N -> 'man' | 'dog' | 'park'
    P -> 'in' | 'with'
    V -> 'saw' | 'ate' | 'walked'

So I made my grammar for a Latin phrase, let's check it.
I'm using the phrase: 

***"Puella agricola pulchra amat."***

    S    → NP VP
    VP   → NP V
    NP   → NP Adj | NP NP | N | VP
    
    N    → puella | agricola | vir
    Adj  → bonus | pulchra | fessus
    V    → amat | videt

But as we saw priviously the adj could modify all nouns in this scenario, since latin is very ambiguous.
We end up with lots of trees, including trees that say the same thing but are still different. 

***"The girl loves the good farmer"***
```
          S
       /    \
     NP      VP
     |      /  \
  puella   NP    V
           / \
     agricola bonus
                  amat

```
***"The good girl loves the farmer."***
```
          S
       /     \
     NP       VP
   /   \     /  \
puella bonus NP  V
             |   |
         agricola amat

```

## Get rid of ambiguity 
So, we have a problem, our grammar has to meanings, this ambiguity, the way we detect it more clearly, is that we can generate different trees to get different meanings, just like I did above, How don we fix it? We need to add intermediate states and productions that indicate a precedence, this eliminates the or between equivalent states.

The next grammar is designed to generate only one kind of tree for each structure: 

    S    → NP VP
    VP   → NP V
    NP   → NP Adj | N
    N    → puella | agricola | vir
    Adj  → bonus | pulchra | fessus
    V    → amat | videt

Now we get a single meaning.  

***"Puella agricola fessus amat." (The girl loves the tired farmer)*** 

```
         S
       /   \
     NP     VP
   /   \     /  \
  NP  Adj  NP    V
  |        |   \    \
puella agricola bonus amat

```

Side note: When I talk about meaning I'm talking about the structure, I've added different nouns and adjectives for depth purposes 

## Get rid of left recursion / Final grammar
So we still have another problem to solve, do you notice, that we can go from NP, to NP again? 

    NP   → NP Adj | N

Well this generates a problem, we can just call NP infinite times to the left and just get a non-ending sentence, kind of weird right? Let's fix it.

The way we fix it is the following: Substitute the productions presenting the left recursion, with two new productions, where the first element will be a terminal and use an intermediate state. 

    S         → NP VP
    NP        → N AdjList
    AdjList   → Adj AdjList | ε
    VP        → NP V
    N         → puella | agricola | vir
    Adj       → bonus | pulchra | fessus
    V         → amat | videt

***"Puella agricola bonus amat." (The girl loves the good farmer)*** 
```
         S
       /   \
     NP     VP
   /   \     /  \
  N  AdjList NP   V
  |     |     |   |
puella  ε  agricola bonus amat
```

AdjList is our intermediate state, and ε is the terminal one.

## Chomsky Hierarchy 
