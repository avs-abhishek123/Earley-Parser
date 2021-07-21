# Earley-Parser

- Earley parser is an algorithm for parsing strings that belong to a given context-free language, though (depending on the variant) it may suffer problems with certain nullable grammars. 
- An efficient top-down parsing algorithm that avoids some of the inefficiency associated with purely naive search with the same top-down strategy (cf. recursive descent parser).
  - Intermediate solutions are created only once and stored in a chart (dynamic programming).
  - Left-recursion problem is solved by examining the input.
  - Earley is not picky about what type of grammar it accepts, i.e., it accepts arbitrary CFGs (CKY).

## EARLEY-PARSING-ALGORITHM
```
function Earley-Parse(words,grammar) returns chart
  Enqueue((γ → •S, [0,0]),chart[0])
  for i ← from 0 to Length(words) do
    for each state in chart[i] do
      if Incomplete?(state) and Next-Cat(state) is not POS then
        Predictor(state)
      elseif Incomplete?(state) and Next-Cat(state) is POS then
        Scanner(state)
      else
        Completer(state)
     end
  end
return(chart)
```

