# Programação Orientada a Objetos

Neste repositório deixarei algumas explicações do lado téorico da Programação Orientado a Objetos
<br><br>

<h2>
Conceitos Iniciais
</h2>

### Pacotes
Uma forma de organizar no caso da linguagem Java, prevenindo problemas como repetição de nomes de classes ou identificadores, entre outros. Usamos pacotes para associar um grupo de classes para o mesmo Objetivo do sistema, para garantir que aquele grupo está se referindo a mesma regra de negócios.

### Classe
É um protótipo para criação do nosso objeto, onde é nela que podemos colocar as característica e comportamentos (atributos e métodos) para nosso Objeto.

### Objeto
É o nosso protótipo final, onde já podemos utilizar dentro do nosso sistema as características e funcionalidades daquele tipo do Objeto quando for instânciado.
<br><br>
<h2>
Os 4 pilares da Programação Orientada a Objeto
</h2>

### ABSTRAÇÃO

Um dos pontos mais importantes, pois é nesta etapa que devemos pensar como o Objeto irá se comportar em nosso sistema e resolver o problema dentro do sistema. As abstrações são representadas pelas classes, ou seja é onde definimos nossos atributos, métodos (lembre-se criação do protótipo do Objeto). Três pontos importantes da Abstração  
1. Identidade: Nome ao Objeto que iremos criar, para distinguir das demais classes, lembre-se da proteção dos pacotes apresentados acima.

2. Estado ou característica atual: São conjuntos de valores de seus atributos em um determinado instante. Exemplo: as propriedades do objeto Carro, poderiamos ter "Nome", "QtdPortas", "Cor".

3. Comportamento: Reação apresentada em resposta as solicitações feitas naquele objeto.
```java
// Identidade da classe ( nome )
public class Carro {
  // estados ou características
	public String nome;
	public int qtdPortas;
	public String cor;
	public Carro(String nome, int qtdPortas, String cor) {
		this.nome = nome;
		this.qtdPortas = qtdPortas;
		this.cor = cor;
	}
  
  // comportamento
	public void acelerar() {
		System.out.println("Acelerando o carro...");
	}

  public void desacelerar() {
		System.out.println("Desacelerando o carro...");
  }
	
}
```
<br>

### ENCAPSULAMENTO
### Parte 1

Uma técnica utilizada para adicionar segurança em nossa aplicação em uma programação orientada a objeto por fazer com que as propriedades e métodos possam ser escondidas e talvez serem acessadas somente de uma outra forma tendo validações ou não. Um bom exemplo: é definir nossas propriedades privadas sendo ligadas a métodos especiais que são os getters e setters (pegar e alterar o valor), pois com isso não iremos conseguir acessar a propriedade diretamente do objeto, tendo então uma camada de segurança à aplicação.

```java
public class Carro {
  // não consigo acessar diretamente, exemplo:
  // Carro carro = new Carro('Clio', 2, 'Verde)
  // carro.cor = 'Azul' -> erro, neste caso seria carro.setCor('Azul')
  // para alterar a cor do objeto carro.
  // e carro.getCor() para pegar a cor do carro.

	private String nome;
	private int qtdPortas;
	private String cor;
	public Carro(String nome, int qtdPortas, String cor) {
		this.nome = nome;
		this.qtdPortas = qtdPortas;
		this.cor = cor;
	}
	
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}

	public int getQtdPortas() {
		return qtdPortas;
	}
	public void setQtdPortas(int qtdPortas) {
		this.qtdPortas = qtdPortas;
	}

	public String getCor() {
		return cor;
	}
	public void setCor(String cor) {
		this.cor = cor;
	}

	public void acelerar() {
		System.out.println("Acelerando o carro...");
	}
	
	public void desacelerar() {
		System.out.println("desacelerando o carro...");
	}
	
}
```

### Parte 2

Outra parte importante do encapsulamento é a criação de interfaces para nossas classes, pois ela é uma espécie de contrato que uma classe obrigatoriamente deve seguir, porém só poder conter comportamentos ( métodos ) e não características ( atributos ), ela definir quais métodos a classe deve conter obrigatóriamente. Veja o exemplo abaixo: <br>
Criação da minha interface:
```java
interface ControlarVeiculo {
	void acelerar();
	void desacelerar();
}
```
Classe carro implementando o Contrato ( interface ):
```java
// Observe que tem a palavra implements e o nome da interface
// implements é para dizer que a classe vai possuir um contrato
// e com isso a classe deve seguir as regras de ControlarVeiculo neste caso.
// Ou seja adeve possuir os métodos de acelerar() e desacelerar() se não vai dar erro

public class Carro implements ControlarVeiculo {
	private String nome;
	private int qtdPortas;
	private String cor;
	public Carro(String nome, int qtdPortas, String cor) {
		this.nome = nome;
		this.qtdPortas = qtdPortas;
		this.cor = cor;
	}
	
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}

	public int getQtdPortas() {
		return qtdPortas;
	}
	public void setQtdPortas(int qtdPortas) {
		this.qtdPortas = qtdPortas;
	}

	public String getCor() {
		return cor;
	}
	public void setCor(String cor) {
		this.cor = cor;
	}

	public void acelerar() {
		System.out.println("Acelerando o carro...");
	}
	
	public void desacelerar() {
		System.out.println("desacelerando o carro...");
	}
	
}
```
<br>

### HERANÇA

É um mecânismo de derivação que faz com que uma classe pode ser construída como extensão de outra classe. Por exemplo uma família que contém uma criança que herda características de seu pai e seu pai herda características de seu avô e assim por diante, porém pode ser que a criança mude alguma característica herdada de seu pai e isso na herança de programação orientada a objeto pode acontecer tranquilamente ( Uma classe derivada pode redefinir operações de sua classe base ), porém isso veremos no próximo pilar de Orientação a Objeto.
```java
public class Veiculo {
	private int qtdRodas;

	public Veiculo(int qtdRodas) {
		this.qtdRodas = qtdRodas;
	}

	public int getQtdRodas() {
		return qtdRodas;
	}
	public void setQtdRodas(int qtdRodas) {
		this.qtdRodas = qtdRodas;
	}	
}
```

```java
// Observe Carro extendeu (extends) características e comportamentos de Veiculo
// O método Super é usado para referenciar o construtor da classe pai.
// Com isso aproveitaremos o construtor também da clase pai.

public class Carro extends Veiculo implements ControlarVeiculo {
	private String nome;
	private int qtdPortas;
	private String cor;
	public Carro(int qtdRodas, String nome, int qtdPortas, String cor) {
		super(qtdRodas);
		this.nome = nome;
		this.qtdPortas = qtdPortas;
		this.cor = cor;
	}
	
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}

	public int getQtdPortas() {
		return qtdPortas;
	}
	public void setQtdPortas(int qtdPortas) {
		this.qtdPortas = qtdPortas;
	}

	public String getCor() {
		return cor;
	}
	public void setCor(String cor) {
		this.cor = cor;
	}

	public void acelerar() {
		System.out.println("Acelerando o carro...");
	}
	
	public void desacelerar() {
		System.out.println("desacelerando o carro...");
	}	
}
```
<br>

### POLIMORFISMO

É a característica que garante que um método de uma classe filha possa ter um comportamento diferente da classe pai ( resultados diferentes ), como foi comentado acima em Herança isso pode ser feito sem problemas alguns graças a está técnica de polimorfismo.

Sobrescrita de métodos e Sobrecarga: O método de sobrescrita tem que ser idêntico ao método da classe herdada, ou seja precisam ter o mesmo nome, valor de retorno e argumentos. Agora caso se a classe filha tiver o método com o mesmo nome porém não idêntica pois criou-se então uma sobrecarga, permitindo então a existências de varíos métodos de mesmo nome, porém com assinaturas diferentes.

```java
// Na classe Pai foi acrescentado o método apresentarVeiculo
public class Veiculo {
	private int qtdRodas;

	public Veiculo(int qtdRodas) {
		this.qtdRodas = qtdRodas;
	}

	public int getQtdRodas() {
		return qtdRodas;
	}
	public void setQtdRodas(int qtdRodas) {
		this.qtdRodas = qtdRodas;
	}
	
	public void apresentarVeiculo(String tipoVeiculo) {
		System.out.println("Tipo do Veículo é --> " + tipoVeiculo);
	}
}
```

```java
public class Carro extends Veiculo implements ControlarVeiculo {
	private String nome;
	private int qtdPortas;
	private String cor;
	public Carro(int qtdRodas, String nome, int qtdPortas, String cor) {
		super(qtdRodas);
		this.nome = nome;
		this.qtdPortas = qtdPortas;
		this.cor = cor;
	}
	
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}

	public int getQtdPortas() {
		return qtdPortas;
	}
	public void setQtdPortas(int qtdPortas) {
		this.qtdPortas = qtdPortas;
	}

	public String getCor() {
		return cor;
	}
	public void setCor(String cor) {
		this.cor = cor;
	}

	public void acelerar() {
		System.out.println("Acelerando o carro...");
	}
	
	public void desacelerar() {
		System.out.println("desacelerando o carro...");
	}
	
  // método apresentarVeiculo fez uma sobrecarga no método da classe Pai
  // Foi adicionado um parâmetro a mais
	public void apresentarVeiculo(String tipoVeiculo, String marca) {
		System.out.println("Tipo do veículo é " + tipoVeiculo + " da marca " + marca);
	}	
}
```

### TESTES 

```java

public class teste {

	public static void main(String[] args) {
		Carro carro = new Carro(4,"Clio", 2, "Verde");
		carro.setCor("Azul"); // alterando valor com segurança
		System.out.println(carro.getCor());
		System.out.println(carro.getQtdRodas());
    // Observe abaixo que tanto faz a quantidade de parâmetros neste caso
    // já que aconteceu uma sobrecarga no método
		carro.apresentarVeiculo("Carro");
		carro.apresentarVeiculo("Carro", "BMW");
	}
}
```

