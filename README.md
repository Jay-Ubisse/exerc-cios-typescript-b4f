# Exercícios de TypeScript - Respostas

### Parte 1 – Tipos básicos e Type Annotation

**1. Declaração de variáveis com tipos:**
```ts
let nome: string = "João";
let idade: number = 30;
let ativo: boolean = true;
let vazio: null = null;
let indefinido: undefined = undefined;
```

**2. Função soma:**
```ts
function somar(a: number, b: number): number {
  return a + b;
}
```

**3. Função com retorno void:**
```ts
function mostrarMensagem(): void {
  console.log("Bem-vindo!");
}
```

**4. Tipo any:**
```ts
let valor: any = 5;
valor = "texto";
valor = true; // compila, mas pode gerar bugs
```

**5. Tipo unknown com type guard:**
```ts
let dado: unknown = "Hello";

if (typeof dado === "string") {
  console.log(dado.toUpperCase());
}
```

**6. Type inference:**
```ts
function tipoDeValor(valor: any) {
  if (typeof valor === "string") {
    console.log("É uma string.");
  } else if (typeof valor === "number") {
    console.log("É um número.");
  } else if (typeof valor === "boolean") {
    console.log("É um booleano.");
  }
}
```

---

### Parte 2 – Arrays, Objetos, Type Aliases e Interfaces

**7. Média de array:**
```ts
function mediaNumeros(numeros: number[]): number {
  const total = numeros.reduce((acc, val) => acc + val, 0);
  return total / numeros.length;
}
```

**8. Type alias com objeto:**
```ts
type Pessoa = {
  nome: string;
  idade: number;
  ativo: boolean;
};

const pessoa: Pessoa = { nome: "Ana", idade: 25, ativo: true };
```

**9. Interface Produto:**
```ts
interface Produto {
  nome: string;
  preco: number;
  categoria: string;
}

function descreverProduto(produto: Produto): string {
  return `${produto.nome} custa R$${produto.preco} e pertence à categoria ${produto.categoria}.`;
}
```

**10. Produtos com preço acima de 100:**
```ts
function filtrarProdutos(produtos: Produto[]): Produto[] {
  return produtos.filter(p => p.preco > 100);
}
```

**11. Type alias Pessoa e array:**
```ts
type Pessoa = {
  nome: string;
  email: string;
  telefone: string;
};

const pessoas: Pessoa[] = [
  { nome: "João", email: "joao@email.com", telefone: "12345" },
  { nome: "Maria", email: "maria@email.com", telefone: "67890" }
];

pessoas.forEach(p => console.log(p));
```

**12. Interface Pessoa:**
```ts
interface Pessoa {
  nome: string;
  email: string;
  telefone: string;
}
```

**13. Combinar tipos:**
```ts
type Endereco = {
  rua: string;
  cidade: string;
};

type PessoaCompleta = Pessoa & Endereco;

const usuario: PessoaCompleta = {
  nome: "Lucas",
  email: "lucas@email.com",
  telefone: "00000",
  rua: "Rua A",
  cidade: "Maputo"
};
```

---

### Parte 3 – Enums, Union Types e Funções

**14. Enum dias da semana:**
```ts
enum Dia {
  Segunda, Terca, Quarta, Quinta, Sexta, Sabado, Domingo
}

function tipoDia(dia: Dia): string {
  return dia === Dia.Sabado || dia === Dia.Domingo ? "Final de semana" : "Dia útil";
}
```

**15. Enum níveis de acesso:**
```ts
enum Acesso {
  Admin,
  User,
  Guest
}

function permissao(acesso: Acesso): string {
  switch(acesso) {
    case Acesso.Admin: return "Acesso total";
    case Acesso.User: return "Acesso limitado";
    case Acesso.Guest: return "Acesso restrito";
  }
}
```

**16. Função com union type:**
```ts
function tratarEntrada(valor: string | number): number {
  return typeof valor === "string" ? valor.length : valor * valor;
}
```

**17. Função com parâmetros opcionais:**
```ts
function somaOpcional(a?: number, b?: number): number {
  if (a && b) return a + b;
  return 0;
}
```

**18. Função com callback:**
```ts
function mapear(numeros: number[], fn: (n: number) => number): number[] {
  return numeros.map(fn);
}
```

**19. Interface ContaBancária:**
```ts
interface ContaBancaria {
  numero: string;
  saldo: number;
  depositar(valor: number): void;
}

const conta: ContaBancaria = {
  numero: "123",
  saldo: 500,
  depositar(valor: number) {
    this.saldo += valor;
  }
};
```

**20. Formulário de contato:**
```ts
interface FormularioContato {
  nome: string;
  email: string;
  mensagem: string;
}

function enviarFormulario(form: FormularioContato): void {
  console.log(`Nome: ${form.nome}\nEmail: ${form.email}\nMensagem: ${form.mensagem}`);
}
