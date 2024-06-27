# How to use icsiboost

## Prepare data

You need a file which defines the classes and a file contining the train, dev and test data

class definition `rules.names`

The first line defines tha classes to predict, the following lines the columns in the data file

```
CORRECT, INCORRECT.
id: ignore.
rulename: text.
language: text.
enhanceddep: text.
upos: text.
xpos: text.
deprel: text.
headupos: text.
headdeprel: text.
headdist: continuous.
enhancedheaddist: continuous.
```

Second example

```
ARG0, ARG1, ARG2, ARG3, ARG4, ARG5, ARG6, ARG7, ARG8, ARG9.
subjobj: text: expert_type=ngram expert_length=2
```

The data file (`rules.txt`) must provide values for all columns

```
1,OblCase4,fr_sequoia,obl:arg,PROPN,_,obl:arg,VERB,root,-6,-6,CORRECT
2,OblCase4,fr_sequoia,obl:arg,NOUN,_,obl:arg,VERB,root,-10,-10,CORRECT
3,OblCase4,fr_sequoia,nmod,PROPN,_,nmod,NOUN,obl:arg,-3,-3,CORRECT
4,ConjOtherFr,fr_sequoia,nsubj:enh,NOUN,_,conj,NOUN,nsubj,-2,3,CORRECT
5,OblCase4,fr_sequoia,nmod,PROPN,_,nmod,NOUN,nsubj,-4,-4,CORRECT
6,OblCase4,fr_sequoia,nmod,NOUN,_,nmod,NOUN,appos,-1,-1,CORRECT
7,OblCase4,fr_sequoia,nmod,PROPN,_,nmod,NOUN,appos,-3,-3,CORRECT
8,Advcl,fr_sequoia,acl,VERB,_,acl,PROPN,nsubj,-8,-8,CORRECT
9,OblCase4,fr_sequoia,nmod,PROPN,_,nmod,NOUN,obl:mod,-3,-3,CORRECT
10,ConjSubj1,fr_sequoia,nsubj:enh,NOUN,_,nsubj,VERB,root,5,26,INCORRECT
11,OblCase4,fr_sequoia,obl:arg,PROPN,_,obl:arg,VERB,conj,-2,-2,CORRECT
12,ConjOtherFr,fr_sequoia,obj:enh,NOUN,_,conj,NOUN,obj,-2,-3,CORRECT
13,OblCase4,fr_sequoia,nmod,PROPN,_,nmod,NOUN,obj,-5,-5,CORRECT
14,ConjOtherFr,fr_sequoia,obj:enh,NOUN,_,conj,NOUN,obj,-9,-10,INCORRECT
15,OblCase4,fr_sequoia,nmod,PROPN,_,nmod,NOUN,conj,-3,-3,CORRECT
```

Second example

```
establish-01 model,ARG1
model innovate-01,mod
innovate-01 industry,ARG1
company -,wiki
name IM,op1
country United_States,wiki
name United,op1
name States,op2
and believe-01,op1
believe-01 person,ARG0
```

## Train a model

You may also need a data file `rules.test` and `rules.dev` in the same format as `rules.txt`

```
src/icsiboost -n 500 -S rules --names rules.names --train rules.txt --model rules.shyp
```

## test the model

```
src/icsiboost3.py -S rules -t rules.test [-s]
```


For more info see the doc of the original Icsiboost