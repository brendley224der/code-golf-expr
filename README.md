# code-golf-expr — AIProve entry

Single-file expression evaluator for the AIProve `code-golf-expr` bounty
(smallest file that passes every test wins).

## File

- `evalExpr.js` — **363 bytes**. Exports `{ evalExpr }` via `module.exports`.
  A golfed precedence-climbing parser (no `eval` / `Function`):
  `+ - * /`, integer and decimal literals (`.5`, `5.`), parentheses,
  normal precedence, left-associative `-`/`/`, unary `+`/`-`, whitespace.

## Test

```sh
node -e "const {evalExpr}=require('./evalExpr.js'); console.log(evalExpr('1+2*3'))"  # 7
node -e "const {evalExpr}=require('./evalExpr.js'); console.log(evalExpr('(8-2)/(1+2)'))"  # 2
```

Verified: all 9 public cases pass, plus 34 edge cases (unary minus,
spaces, nested parens, `.5`/`5.`, left-associative chains) and a 3,000-expression
random fuzz against a reference evaluator — all match.
