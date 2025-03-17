# Lista de Exercícios - JavaScript

## Questões Objetivas

### (1) Considerando a execução do código abaixo, indique a alternativa correta e justifique sua resposta.

```js
console.log(x);
var x = 5;
console.log(y);
let y = 10;
```

**Resposta:**
Alternativa correta: **(a) A saída será undefined seguido de erro**

**Justificativa:**
O JavaScript faz o hoisting das declarações de `var`, então `x` é elevado ao topo do escopo, mas sem valor atribuído, resultando em `undefined`. No entanto, `let` não permite acesso antes da inicialização, causando um erro de referência ao tentar acessar `y` antes de sua declaração.

---

### (2) O seguinte código JavaScript tem um erro que impede sua execução correta. Analise e indique a opção que melhor corrige o problema. Justifique sua resposta.

```js
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
```

**Resposta:**
Alternativa correta: (**a) Substituir `if (a || b === 0)` por `if (a === 0 || b === 0)`**

**Justificativa:**
A expressão `a || b === 0` está incorreta, pois `b === 0` tem maior precedência e retorna `true` apenas quando `b` é `0`, mas `a || true` sempre resulta em `true` caso `a` seja diferente de `0`. A correção usa `a === 0 || b === 0` para verificar corretamente se qualquer um dos valores é `0`.

---

### (3) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.

```js
function calcularPreco(tipo) {
    let preco;

    switch(tipo) {
        case "eletrônico":
            preco = 1000;
        case "vestuário":
            preco = 200;
            break;
        case "alimento":
            preco = 50;
            break;
        default:
            preco = 0;
    }

    return preco;
}
console.log(calcularPreco("eletrônico"));
```

**Resposta:**
Alternativa correta: (**b) O código imprime 200.**

**Justificativa:**
Falta um `break` após `preco = 1000;`, então a execução continua para o próximo `case`, alterando `preco` para `200` antes de sair.

---

### (4) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.

```js
let numeros = [1, 2, 3, 4, 5];
let resultado = numeros.map(x => x * 2).filter(x => x > 5).reduce((a, b) => a + b, 0);
console.log(resultado);
```

**Resposta:**
Alternativa correta: (**c) 18**

**Justificativa:**
1. `map(x => x * 2)` resulta em `[2, 4, 6, 8, 10]`
2. `filter(x => x > 5)` mantém `[6, 8, 10]`
3. `reduce((a, b) => a + b, 0)` soma `6 + 8 + 10 = 18`

---

### (5) Qual será o conteúdo do array lista após a execução do código? Indique a alternativa correta e justifique sua resposta.

```js
let lista = ["banana", "maçã", "uva", "laranja"];
lista.splice(1, 2, "abacaxi", "manga");
console.log(lista);
```

**Resposta:**
Alternativa correta: (**c) ["banana", "abacaxi", "manga", "laranja"]**

**Justificativa:**
O `splice(1, 2, "abacaxi", "manga")` remove dois elementos a partir do índice `1` (`maçã` e `uva`) e adiciona `abacaxi` e `manga` no lugar.

---

### (6) Abaixo há duas afirmações sobre herança em JavaScript. Indique a alternativa correta e justifique sua resposta.

**Resposta:**
Alternativa correta: (**a) As duas afirmações são verdadeiras, e a segunda justifica a primeira.**

**Justificativa:**
Herança permite reutilizar código, e em JavaScript é implementada com `extends`.

---

### (7) Dado o seguinte código. Indique a alternativa correta e justifique sua resposta.

**Resposta:**
Alternativa correta: (**a) I e II são verdadeiras.**

**Justificativa:**
A classe `Funcionario` herda de `Pessoa` corretamente e usa `super()` para acessar métodos e atributos da classe pai.

---

### (8) Analise as afirmações a seguir. Indique a alternativa correta e justifique sua resposta.

**Resposta:**
Alternativa correta: (**b) A asserção é verdadeira e a razão é falsa.**

**Justificativa:**
O polimorfismo existe em JavaScript, mas não por sobrecarga de métodos, já que JavaScript não suporta sobrecarga de forma nativa.

---

## Questões Dissertativas

### (9) Correção do código

```js
function somaArray(numeros) {
    let soma = 0; // Inicializar soma
    for (let i = 0; i < numeros.length; i++) { // Corrigir tamanho do array
        soma += 2 * numeros[i]; // Somar corretamente o dobro
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4]));
```

**Correções:**
- `size` não é propriedade de arrays em JS, usar `length`.
- `soma` deve ser inicializada corretamente.
- Acumulamos a soma ao invés de sobrescrever o valor.

---

### (10) Implementação de herança com Produto e Livro

```js
class Produto {
    constructor(nome, preco) {
        this.nome = nome;
        this.preco = preco;
    }

    calcularDesconto() {
        return this.preco * 0.9; // 10% de desconto
    }
}

class Livro extends Produto {
    calcularDesconto() {
        return this.preco * 0.8; // 20% de desconto
    }
}

const produto = new Produto("Genérico", 100);
console.log(produto.calcularDesconto()); // 90

const livro = new Livro("JavaScript", 100);
console.log(livro.calcularDesconto()); // 80
```

**Explicação:**
A classe `Livro` herda de `Produto` e reescreve `calcularDesconto`, aplicando 20% em vez de 10%.
