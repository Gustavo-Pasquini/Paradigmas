# Derivação de um Código a partir da Gramática de uma Linguagem de Programação

## Informações Gerais

| Item | Descrição |
| --- | --- |
| **Linguagem escolhida** | Swift |
| **Notação utilizada** | BNF |
| **Fonte consultada** | [The Swift Programming Language — Declarations](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/declarations/) |

## Regras de Produção Usadas

### Statement / Loop

```bnf
statement          → loop-statement
loop-statement      → for-in-statement
for-in-statement    → 'for' pattern 'in' expression code-block
pattern              → identifier-pattern
identifier-pattern    → identifier
```

### Expression

```bnf
expression            → prefix-expression infix-expressions(opt)
infix-expressions      → infix-expression
infix-expression        → infix-operator prefix-expression
prefix-expression        → postfix-expression
postfix-expression         → primary-expression
primary-expression          → literal-expression | identifier
literal-expression            → literal
literal                         → integer-literal | string-literal
infix-operator                   → '...' | '*'
```

### Code Block

```bnf
code-block    → '{' statements(opt) '}'
statements     → statement
```

### Trecho de Código

```
    for i in 1...10 {
        a * i
    }
```

### Execução da Derivação

Seguindo o arquivo Aula003/Diagrama.png