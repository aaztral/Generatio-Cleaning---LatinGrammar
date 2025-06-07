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

    S -> NP VP
    NP -> NP Adj | N
    VP -> NP V
    N -> puella | agricola | vir
    Adj -> pulchra | fessus
    V -> amat | videt

But as we saw priviously the word ****pulchra*** could modify both ***puella*** or ***agricola*** in this scenario, since latin is very ambiguous.
So we end up with 2 meanings 

***"The girl loves the beautiful farmer"***
```
      S
     / \
   NP   VP
   |    /  \
   N  NP    V
 (Puella)(Agricola Pulchra)(Amat)
```
***"The beautiful girl loves the farmer "***
```
      S
     / \
   NP   VP
(Puella Pulchra)  (Agricola Amat)
```

## Get rid of ambiguity 

## Get rid of left recursion 

## Final grammar

## Tests 

## Chomsky Hierarchy 
