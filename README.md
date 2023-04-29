# [Variáveis e constantes | Aprenda Rust | 02](https://youtu.be/GYhTFLdHNQI)

## Cargo watch

```bash
cargo install cargo-watch 
```

```bash
cargo watch -x run
```

Não é permitido declarar variáveis no escopo principal do programa.
```rust
let total = 30; // Error
//
```

`let` palavra chave para declaração de variáveis
`total` nome do recurso
`= 30;` variable binding

## Que RAII é isso?

RAII (Resource acquisition is initialization)

## Lifetime e escopo

```rust
fn main() { // Life-time -> inicio do escopo
	let total = 30;
} // fim do escopo
// Drop -> realiza a desalocação das variáveis no final do escopo
```

## Unused Variables

```rust
fn main() {
	let _total = 30; // _ (underline) é utilizado para ignorar alguma coisa no programa
}
```

```rust
fn main() {
	let total = 30;
	println!("Trabalhou {} horas", total); // {} interpolação
}
```

## Inferência de tipos

```rust
fn main() {
	let total = 30; // inferência pelo sintaxe ou contexto
	println!("Trabalhou {} horas", total);
}
```

```rust
fn main() {
	let total: i32 = 30; // definição explicita
	println!("Trabalhou {} horas", total);
}
```

## Mutabilidade

```rust
fn main() {
	let mut total = 30;
	println!("Trabalhou {} horas", total);
	total = 44;
	println!("Trabalhou {} horas", total);
}
```

## Tipagem forte

```rust
fn main() {
	let mut total = 30;
	println!("Trabalhou {} horas", total);
	total = 44.5; // Error
	println!("Trabalhou {} horas", total);
}
```

## Variable Shadowing (reaproveitando nomes	de variáveis)

```rust
fn main() {
	let total = 30;
	println!("Trabalhou {} horas", total);
	let total = "quarenta";
	println!("Trabalhou {} horas", total);
}
```

## Escopos internos

```rust
fn main() {
	let total = 30;
	{ // Life-time -> inicio do escopo
		let total = total + 20;
		println!("Trabalhou {} horas", total);
	} // fim do escopo
	println!("Trabalhou {} horas", total);
}
```

```bash
Trabalhou 50 horas
Trabalhou 30 horas
```

## Constantes

- Pode ser declarada no escopo principal do programa
- Nome em letra maíscula (snake case)
- Imutável
- O tipo deve ser declarado explicitamente
- Não pode ser definida multiplas vezes

Inline -> substitui a constante pelo valor dela.

```rust
const SECONDS_IN_MINUTES: u32 = 60;
const MINUTES_IN_HOUR: u32 = 60;
const SECONDS_IN_HOUR: u32 = SECONDS_IN_MINUTES * MINUTES_IN_HOUR;

fn main() {
	let total = 30;
	let total_em_segundos = total * SECONDS_IN_HOUR;
	println!("Trabalhou {} segundos", total_em_segundos);
}
```
