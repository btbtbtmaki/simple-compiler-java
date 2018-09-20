A simple compiler in java
Tokens:
  integerConstant → [0..9]+       // has type "integer"
  boolean Constant → true false   // has type "boolean"
 
  identifier → [a..Z]+ 
  punctuator operator | punctuation 
  operator → +| * | > 
  punctuation → ;], {|}] :=

Grammar:
  S → main block 
  block → { statement* }

statement → declaration 
            printStatement
declaration → imm identifier := expression;     // immutable (constant) value 
                                                // identifier gets the type of the expression.

printStatement → print printExpressionList;     // print the expression values
printExpressionList → printExpression 
printExpression → expression, nl'
expression →  expression operator expression    // all operations left-associative
              literal

literal → integer Constant | boolean Constant | identifier
