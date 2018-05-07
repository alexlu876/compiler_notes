# Compiler

Source code --compiler--> executable -> images

### Five Steps:
1. Lexer
2. Syntactic Analyzer 
3. Semantic Analyzer 
4. Optimizer (Optional)
5. Code generator

## The Lexer
Performs lexical analysis (duh)
- Will look through code 
- Find meaningful key words and symbols
- Find valid variables (ex. no ? in var. names)
- Valid strings, literal formats, identifier formats etc.
- Does not perform any structural analysis (a typo of def -> dep would be ok, def -> de? would not)
- Outputs a list of tokens from source code

```
int main(){
   long x = 5 + 6;
   printf("%d", x);
   return 0;
}
```
Lexer will read this code and create a token list, gets rid of formatting (formatting is for humans, not computers):
```
int
main
(
)
{
long
x
etc...
```
If there is meaningful white space (looking at you, python), then it will show up in the token list
