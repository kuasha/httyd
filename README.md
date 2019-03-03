## Introduction

Building a new computer programming language and compiler for it is a great way to understand the way computers work. It has been some time since I have written my last article https://www.codeproject.com/Articles/24029/Home-Made-Java-Virtual-Machine and today is my birthday (March 2) and I want to start another article about topic of my choice.

Creating a programming language and a compiler for it for learning purposes is easier than it seems at the beginning. There are few basic things that needs to be done:

    Define the grammer
    Create a lexer
    Create a parser
    Create a semantec validator
    Generate code in a platform independent low level instruction set (optional)
    Generate platform specific code
    Optimize the generated code to remove inefficiencies

I'll explain each step with examples. Please keep in mind that I'll try to keep the article as simple as possible. The idea is to learn a way to build a computer - not the best way. 

## Defining a grammer
A grammer defines the syntactical structure of the language. We will start with a simple grammer that can evaluate an expression- build a calculator first. And then we will add things like variables, assignments, conditional statements, functions etc.

While working on grammer my favirite tool is ANTLR. You can use it to generate a parser and validate with a graphical tool. Lets take the example grammer from antlr home page: 

```
grammar Expr;		
prog:	(expr NEWLINE)* ;
expr:	expr ('*'|'/') expr
    |	expr ('+'|'-') expr
    |	INT
    |	'(' expr ')'
    ;
NEWLINE : [\r\n]+ ;
INT     : [0-9]+ ;
```
