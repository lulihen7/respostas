# Respostas



# Questões objetivas
**1) Considerando a execução do código abaixo, indique a alternativa correta e justifique sua resposta.**
```javascript
console.log(x);
var x = 5;
console.log(y);
let y = 10;
```
a) A saída será undefined seguido de erro 

Justificativa: O var x foi definido apos ser chamado e isso causou o retorno undefined, enquanto o y so foi criado apos ser chamado gerando um outro erro.

______
**2) O seguinte código JavaScript tem um erro que impede sua execução correta. Analise e indique a opção que melhor corrige o problema. Justifique sua resposta.**

```javascript
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
```

b) Substituir if (a || b === 0) por if (a === 0 && b === 0)

Justificativa: Não podemos utilizar a logica do if em que duas constantes estão se igualando a um valor, devemos classificar cada constante um valor expecifico mesmo que seja o mesmo valor para as duas.

______
**3) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.**
```javascript
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

b) O código imprime 200.

Justificativa: Como não há break após case "eletrônico", o código segue para o próximo case e sobrescreve preco para 200.
______
**4) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.**
```javascript
let numeros = [1, 2, 3, 4, 5];

let resultado = numeros.map(x => x * 2).filter(x => x > 5).reduce((a, b) => a + b, 0);

console.log(resultado);
```
d) 24

Justificativa: O map dobra os valores [2, 4, 6, 8, 10], o filter mantém [6, 8, 10] e o reduce soma 6 + 8 + 10 = 24.
______
**5) Qual será o conteúdo do array lista após a execução do código? Indique a alternativa correta e justifique sua resposta.**

```javascript
let lista = ["banana", "maçã", "uva", "laranja"];
lista.splice(1, 2, "abacaxi", "manga");
console.log(lista);
```

c) ["banana", "abacaxi", "manga", "laranja"]

Justificativa: O splice(1, 2, "abacaxi", "manga") remove "maçã" e "uva" e insere "abacaxi" e "manga" na posição 1.
______
**6) Abaixo há duas afirmações sobre herança em JavaScript. Indique a alternativa correta e justifique sua resposta**

I. A herança é utilizada para compartilhar métodos e propriedades entre classes em JavaScript, permitindo que uma classe herde os métodos de outra sem a necessidade de repetir código.  
II. Em JavaScript, a herança é implementada através da palavra-chave `extends`.


a) As duas afirmações são verdadeiras, e a segunda justifica a primeira.

Justificativa: A herança permite reuso de código e é implementada em JavaScript com extends.

______
**7) Dado o seguinte código. Indique a alternativa correta e justifique sua resposta.**

```javascript
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }

  apresentar() {
    console.log(`Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`);
  }
}

class Funcionario extends Pessoa {
  constructor(nome, idade, salario) {
    super(nome, idade);
    this.salario = salario;
  }

  apresentar() {
    super.apresentar();
    console.log(`Meu salário é R$ ${this.salario}.`);
  }
}
```


I) A classe Funcionario herda de Pessoa e pode acessar os atributos nome e idade diretamente.  
II) O método `apresentar()` da classe Funcionario sobrepõe o método `apresentar()` da classe Pessoa, mas chama o método da classe pai usando `super`.  
III) O código não funciona corretamente, pois Funcionario não pode herdar de Pessoa como uma classe, já que o JavaScript não suporta herança de classes.

Quais das seguintes afirmações são verdadeiras sobre o código acima?

a) I e II são verdadeiras.

Justificativa: A classe Funcionario herda de Pessoa e pode acessar nome e idade. O método apresentar() de Funcionario chama o da classe pai com super.

______

**8) Analise as afirmações a seguir. Indique a alternativa correta e justifique sua resposta.**

**Asserção:** O conceito de polimorfismo em Programação Orientada a Objetos permite que objetos de diferentes tipos respondam à mesma mensagem de maneiras diferentes.  
**Razão:** Em JavaScript, o polimorfismo pode ser implementado utilizando o método de sobrecarga de métodos em uma classe.

b) A asserção é verdadeira e a razão é falsa.

Justificativa: O polimorfismo permite diferentes respostas a uma mesma chamada, mas JavaScript não consegue suportar sobrecarga de métodos como em Java.

______

# Questões dissertativas
9) O seguinte código deve retornar a soma do dobro dos números de um array, mas contém erros. Identifique os problema e corrija o código para que funcione corretamente. Adicione comentários ao código explicado sua solução para cada problema.

```javascript
function somaArray(numeros) {

    for (i = 0; i < numeros.size; i++) {
        soma = 2*numeros[i];
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4]));
```
**Correção:
```javascript
function somaArray(numeros) {
    let soma = 0; // Inicializa a variável soma
    for (let i = 0; i < numeros.length; i++) { // Corrige .size para .length
        soma += 2 * numeros[i]; // Soma corretamente o dobro de cada número
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4])); // Saída esperada: 20
```
O comando size não existe, o correto é length.
soma precisa ser inicializada.
Atribuição soma = 2 * numeros[i] sobrescrevia valores anteriores, corrigimos para soma +=.

______
10) Crie um exemplo prático no qual você tenha duas classes:

- Uma classe `Produto` com atributos `nome` e `preco`, e um método `calcularDesconto()` que aplica um desconto fixo de 10% no preço do produto.
- Uma classe `Livro` que herda de `Produto` e modifica o método `calcularDesconto()`, aplicando um desconto de 20% no preço dos livros.

```javascript
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

let produto = new Produto("Celular", 100);
console.log(produto.calcularDesconto()); // 90

let livro = new Livro("JavaScript Avançado", 100);
console.log(livro.calcularDesconto()); // 80
```

Explicação:

Livro herda de Produto, reutilizando nome e preco.
O método calcularDesconto() de Livro sobrescreve o da classe produto, aplicando 20% de desconto.
Isso demonstra polimorfismo: objetos diferentes (Produto e Livro) respondem de formas distintas ao mesmo método calcularDesconto().

