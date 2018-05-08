# Compiler

Source code --compiler--> executable -> images

### Five Steps:
STEP | NAME | INPUT | OUTPUT
:---: | --- | --- | ---
1 | Lexer | Source Code | Token List
2 | Syntactic Analyzer | Token List | Syntax Tree
3 | Semantic Analyzer | x | x
4 | Optimizer (Optional) | x | x
5 | Code Generator | x | x

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

Examples of language tokens
- Grouping symbols
- Operators
- Identifiers
- Keywords
- Literals
- Comments (might be deleted, but will be noted)

## Regular Expression
For an identifier, they look like this 

``` ID [a-zA-Z][a-zA-Z0-9_]* ```

This just means it starts with a letter, lowercase or capital, then is followed by any number of letters, digits, or underscores. The asterisk means zero or more of the letters/digits/underscores.

```
%%
[ \t\n ]+ ;
```
Regular expression for whitespace. The plus means one or more, and the semicolon means that if we see one or more of these, we replace with a semicolon. 

```
\-?[0-9]+ |      //ints
\-?[0-9]+\. |    //a dot at the end because why not
\-?[0-9]+\.[0-9]+ | //floats
\-?\.[0-9]+ 
```
This says either 0 or 1 negative sign, then one or more digits. Vertical bars are or. Backslashes are just used because minus signs and periods are actually things. 

In our language, we also wanna do stuff like detect strings, such as the word save.
```
"save" {return SAVE;}
```
This can do it, but we need to define strings.
```
[a-zA-Z][\.a-zA-Z0-9_]* {
strcpy(yyval.string, yytext); return STRING;}
```

## Syntactic Analyzer 
Basically a parser, will take the stuff from token list and put it into a tree called a syntax tree.


























