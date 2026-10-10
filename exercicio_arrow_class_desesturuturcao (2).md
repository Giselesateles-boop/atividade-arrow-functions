## Exercício 1 - Hora de usar as setas

Utilize o que foi aprendido neste capítulo e refatore a função `imprimeProduto` para utilizar arrow functions. Não deixe de customizar o método para utilizar templates strings.

```javascript
let carrinho = [
  { nome: "abacaxi", preco: "2.00" },
  { nome: "detergente", preco: "2.50" },
  { nome: "bolacha", preco: "3.80" },
];

const imprimeProduto = (nome, preco) => {
  console.log(`Produto: ${nome} | Preço: ${preco}`);
};

carrinho.forEach((produto) => {
  imprimeProduto(produto.nome, produto.preco);
});
```

## Exercício 2 - Vou lavar sua boca com sabão!

Utilize as arrow funcions para deixar o código a seguir ainda menor.

```javascript
let palavroes = [
  "Inconstitucionalíssimo",
  "Otorrinolaringologista",
  "Pneumoultramicroscopicossilicovulcanoconiose",
  "Oftalmotorrinolaringologista",
];

let tamanhos = palavroes.map((palavrao) => palavrao.length);

console.log(tamanhos); // [22, 22, 44, 28]
```

## Exercício 3 - Não são só umas reticências?

Qual a diferença básica entre os operadores `Rest` e `Spread`?
**Resposta:** O operador Rest (`...`) reúne vários valores em uma única variável, enquanto o operador Spread (`...`) espalha os valores de um array ou objeto, permitindo, por exemplo, combinar arrays.

## Exercício 4 - A união faz a força

Refatore o código a seguir para utilizar o operador `Spread` ao invés do método `concat`.

```javascript
const equipeMarketing = ["Joana", "Marcela", "Bruna"];
const equipeComercial = ["Talita", "Luisa", "Vitória"];

const timeCompleto = [...equipeMarketing, ...equipeComercial];

realizaBrainstorm(timeCompleto);
```

## Exercício 5 - Pegando a propriedade na lata

Refatore o trecho de código a seguir para utilizar a técnica de desestruturamento.

```javascript
const { email, nome, idade } = usuario;
```

## Exercício 6 - Cara-Crachá

Otimize o trecho de código a seguir utilizando o desestruturamento.

```javascript
const profissional = {
  titulo: "Engenheiro de Software",
  departamento: "Engenharia",
};

function isEngenheiro({ titulo, departamento }) {
  return titulo.indexOf("Engenheiro") > -1 && departamento === "Engenharia";
}

isEngenheiro(profissional); // true

profissional.titulo = "Marketing";

isEngenheiro(profissional); // false
```

## Exercício 7 - O meu videogame é muito melhor que o seu

Aproveitando a classe `VideoGame` criada no exercício anterior, implemente a classe `PlayStation` que contém todas as propriedades do `VideoGame` mais as seguintes proprieades:

- nEntradasUSB: inteiro que representa a quantidade de entradas usb do console
- voltagem: inteiro que representa a voltagem do console.
- adicionais: array de strings que representam os nomes dos adicionais do videogame (ex: adicionais=['Controle sem fio', 'Volante'])

Não esqueça de invocar um objeto da classe.

```javascript
class VideoGame {
  constructor(marca, modelo) {
    this.marca = marca;
    this.modelo = modelo;
  }
}

class PlayStation extends VideoGame {
  constructor(marca, modelo, nEntradasUSB, voltagem, adicionais) {
    super(marca, modelo);

    this.nEntradasUSB = nEntradasUSB;
    this.voltagem = voltagem;
    this.adicionais = adicionais;
  }
}

const meuPlayStation = new PlayStation("Sony", "PlayStation 5", 3, 110, [
  "Controle sem fio",
  "Headset",
]);

console.log(meuPlayStation);
```

## Exercício 8 - Você cumpre as suas promessas?

Implemente o método simulaPromise() que recebe um parâmetro chamado `sucesso` que é um Boolean que indicará se a Promise foi realizada com sucesso ou não. O método deve receber esta parâmetro e imprimir a mensagem: `ok` em caso de sucesso e `not ok` no caso contrário.

Exemplo:

```javascript
simulaPromise(false); // not ok
simulaPromise(true); // ok
```

Não se esqueça de utilizar o `resolve`, `reject`, `then` e `catch` para resolver o exercício.

```javascript
function simulaPromise(sucesso) {
  const promessa = new Promise((resolve, reject) => {
    if (sucesso) {
      resolve("ok");
    } else {
      reject("not ok");
    }
  });

  promessa
    .then((resultado) => console.log(resultado))
    .catch((erro) => console.log(erro));
}

simulaPromise(false); // not ok
simulaPromise(true); // ok
```

## Exercício 9 - Você cumpre as suas promessas em tempo?

Para melhorar a simulação de Promise criada no exercício anterior, faça com o método receba mais um argumento chamado `delay` que é um inteiro que representa os milisegundos que a solicitação demora para responder. Ao executar o método, ele deve demorar o tempo do `delay` para exibir a mensagem no console.

```javascript
function simulaPromise(sucesso, delay) {
  const promessa = new Promise((resolve, reject) => {
    setTimeout(() => {
      if (sucesso) {
        resolve("ok");
      } else {
        reject("not ok");
      }
    }, delay);
  });

  promessa
    .then((resultado) => console.log(resultado))
    .catch((erro) => console.log(erro));
}

simulaPromise(true, 2000);
simulaPromise(false, 1000);

// Ordem que aparece no console:
// not ok
// ok
```

## Exercício 10 - Passando promessa de pai para filho

Qual é o problema com o trecho de código a seguir? E como consertá-lo?

```javascript
// ...
promise
  .then((data) => console.log(`resultado positivo: ${data}`))
  .then((data) => console.log(`resultado positivo 2: ${data}`))
  .catch((data) => console.log(`resultado negativo: ${data}`));
```

**Resposta:** O problema é que o primeiro método `then()` executa o `console.log()`, mas não retorna o valor de `data`. Por isso, o segundo `then()` recebe `undefined`. Para corrigir, precisamos retornar `data` no primeiro `then()`.

```javascript
promise
  .then((data) => {
    console.log(`resultado positivo: ${data}`);
    return data;
  })
  .then((data) => console.log(`resultado positivo 2: ${data}`))
  .catch((data) => console.log(`resultado negativo: ${data}`));
```
