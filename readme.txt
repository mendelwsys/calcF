1. Implemented a subset of calculations of arithmetic expressions in C language.

Implemented:

Arithmetic operations: + - * / f also unary - and + (expressions like -1,+10)
Comparison Operations > <,==,!=,>=,<=
Trinary comparison operator ? : (A?B:C) (if A then B, otherwise C)
Calling functions from the Math package
Using Variables from the Math Package

Grammar type SLR(0)

The parser interface, as before, is contained in the class
su.org.ms.parsers.mathcalc.Parser

The parser tests are in the package su.org.ms.parsers.mathcalc.tst
Calling all TFullCalculate tests in this package.

The test formulas themselves can be edited in IGetFormulaByNameTest.java,
if you add / remove formulas, do not forget to edit variable sz line 103 of this file.

2. Peculiarities of using Cache of parse trees.

The parse tree cache is designed to eliminate the translation step
when calculating identical formulas. 
Formulas are said to be identical if they have the same computational structure.
For example: (a+b)/c-1.3 and formulas (1.1-s)*3.1+x are identical and have one
and also a parse tree up to a permutation of tokens.
However, formulas (a+b)/c-1.3 (a+-b)/c-1.3 have different parse trees
and for each of them entries in the cache will be created.

The use of the cache is effective not only in computing
the same formulas with variable parameters, but also formulas
in which operations are replaced by others with the same priority.

The general reset of the cache is carried out by the parser's clearCash() function.