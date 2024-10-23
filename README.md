# Atendimento do Professor

## Terças e quintas. Professor de horário parcial. Nesses 2 dias, podem contar comigo!



# Semana 02B - Programação

Revisão geral da linguagem C com aprofundamento em conceitos de fluxo de controle e funções, exemplo simples de Blink no Arduino utilizando o paradigma de Orientação a Objetos, Simulador Wokwi.

### CLP Conceitos

**O que é um CLP?**  
Um CLP é como um ESP32 com vários relés automatizando máquinas e esteiras numa fábrica. Contudo, o CLP é muito mais robusto para resistir a ruídos eletromagnéticos, poeira, quedas de energia, falhas de sistemas, conexões físicas e programação.

![CLP](https://github.com/agodoi/m04-semana02b/blob/main/clp01.png)

### Ciclo de Varredura

O CLP possui um ciclo de varredura que se assemelha ao `void loop()` do ESP32. Veja o fluxograma:  
- A última linha é mais importante que a penúltima.  
- A penúltima é mais importante que a antepenúltima.  
- Um botão de emergência deve estar nas últimas linhas.

### CLP - Definições Básicas

O CLP possui entradas e saídas analógicas e digitais. Um dos principais sinais a serem lidos é o sinal de corrente de 4 a 20 mA, pois é um sinal analógico robusto. Contudo, sinais digitais como HIGH e LOW também são usados.

---

## Linguagem C - Classes, Métodos e Atributos

### Classes
Uma classe é uma estrutura de programação que permite definir um novo tipo de dado personalizado com propriedades e comportamentos específicos. Em outras palavras, uma classe cria um novo objeto que pode ser utilizado no programa, como no Arduino.

### Componentes de uma Classe
- **Membros da classe:** Variáveis ou constantes que definem o estado do objeto.
- **Métodos da classe:** Funções que realizam operações no objeto ou nos seus membros.

Ao criar uma classe, você define como o objeto será inicializado, como as propriedades podem ser acessadas e modificadas, e quais métodos estarão disponíveis para interagir com o objeto. Isso facilita a criação de programas mais extensíveis e de fácil manutenção.

### Exemplo Prático
Se você estiver criando um programa que requer o uso de sensores, pode-se criar uma classe que define o comportamento do sensor e métodos para ler seus dados. Sempre que o sensor for necessário, basta instanciar um objeto da classe e utilizá-lo.

### Instâncias
Uma instância é um objeto criado a partir de uma classe.  
Exemplo: Se temos uma classe "Carro", podemos criar várias instâncias como "Carro1", "Carro2", "Carro3", etc. Cada instância terá seus próprios atributos (cor, modelo, ano) e métodos (ligar, acelerar, frear).

---

## Dinâmica Pair Teaching

### Como Fazer?

1. Faça par com um colega que tenha estudado ou "codado" uma função ou classe em Arduino essa semana.
2. Uma pessoa faz o papel de instrutor e a outra o papel de aluno por 20 minutos.
3. Após esse tempo, inverta os papéis.
4. A dupla deverá explicar à turma o que aprendeu sobre classes, funções ou métodos.

### Premiação

As 5 melhores duplas ganharão um prêmio. Haverá uma votação.
