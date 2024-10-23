# Atendimento do Professor

## Terças e quintas. Professor de horário parcial. Nesses 2 dias, podem contar comigo!



# Semana 02B - Programação

Revisão geral da linguagem C com aprofundamento em conceitos de fluxo de controle e funções, exemplo simples de Blink no Arduino utilizando o paradigma de Orientação a Objetos, Simulador Wokwi.


## Vantagens para o seu projeto do IPT

* Usando classes, seu código será mais estrturado;
* Mais organizado;
* Mais profissional;
* Mais eficiente.


### CLP Conceitos

**O que é um CLP?**

Um CLP é como um ESP32 com vários relés automatizando máquinas e esteiras numa fábrica. Contudo, o CLP é muito mais robusto para resistir a ruídos eletromagnéticos, poeira, quedas de energia, falhas de sistemas, conexões físicas e programação do que o ESP32.

Nesse momento, você só precisa saber que existe esse equipamento, porque mais para frente, quem for fazer Engenharia da Computação, terá um estudo mais aprofundado.

A figura abaixo, mostra um CLP profissional, com vários módulos de interface e várias entradas e saídas de dados.

![CLP](https://github.com/agodoi/m04-semana02b/blob/main/clp01.png)

O CLP a seguir, é um dos mais baratos e simples de se programar.

![CLP](https://github.com/agodoi/m04-semana02b/blob/main/clp02.png)

### Ciclo de Varredura

O CLP possui um ciclo de varredura que se assemelha ao `void loop()` do ESP32. Veja o fluxograma:  
- A última linha é mais importante que a penúltima.  
- A penúltima é mais importante que a antepenúltima.  
- Um botão de emergência deve estar nas últimas linhas.

### CLP - Definições Básicas

O CLP possui entradas e saídas analógicas e digitais. Um dos principais sinais a serem lidos é o sinal de corrente de 4 a 20 mA, pois é um sinal analógico robusto. Contudo, sinais digitais como HIGH e LOW também são usados.

![Varredura do CLP](https://github.com/agodoi/m04-semana02b/blob/main/varreduraCLP.png)

![CLP e Sensores](https://github.com/agodoi/m04-semana02b/blob/main/clp04.png)

---

## Linguagem C - Classes, Métodos e Atributos

### Classes
Uma classe é uma estrutura de programação que permite definir um novo tipo de dado personalizado com propriedades e comportamentos específicos. 

Em outras palavras, uma classe cria um novo objeto que pode ser utilizado no programa, como no Arduino.

Portanto, vamos fazer de Programação Orientada a Objeto (POO).

### Componentes de uma Classe
- **Membros da classe:** Variáveis ou constantes que definem o estado do objeto.
- **Métodos da classe:** Funções que realizam operações no objeto ou nos seus membros.

Ao criar uma classe, você define como o objeto será inicializado, como as propriedades podem ser acessadas e modificadas, e quais métodos estarão disponíveis para interagir com o objeto. Isso facilita a criação de programas mais extensíveis e de fácil manutenção.

### Exemplo Prático 1 - Pisca-pisca usando Classe

```
// Definir a classe Blinker
class Blinker {
  private:
    int _pino;
    int _intervalo;
    unsigned long _previousMillis;
    bool _state;
  public:
    Blinker(int pin, int interval) {
      _pino = pin;
      _intervalo = interval;
      _previousMillis = 0;
      _state = false;
      pinMode(_pino, OUTPUT);
    }
    void update() {
      unsigned long currentMillis = millis();
      if (currentMillis - _previousMillis >= _intervalo) {
        _previousMillis = currentMillis;
        _state = !_state;
        digitalWrite(_pino, _state);
      }
    }
};
// Criar um objeto da classe Blinker para o LED conectado ao pino digital 13 com intervalo de 500ms
Blinker led(23, 500);
void setup() {
  // Não é necessário nenhuma configuração no setup para este exemplo
}
void loop() {
  // Atualizar o estado do LED
  led.update();
}
```
---

### Exemplo Prático 2 - Lendo sensor de temperatura usando Classe

```
class TemperatureSensor {
  private:
    int _pino;
  public:
    TemperatureSensor(int pin) {
      _pino = pin;
    }
    float getTemperature() {
      int sensorValue = analogRead(_pino);
      float voltage = sensorValue * (5.0 / 4093.0);
      float temperature = (voltage - 0.5) * 100.0;
      return temperature;
    }
};


// Criar um objeto da classe TemperatureSensor para o sensor LM35 conectado ao pino analógico A0
TemperatureSensor lm35(A0);


void setup() {
  // Iniciar a comunicação serial
  Serial.begin(9600);
}


void loop() {
  // Ler a temperatura atual do sensor
  float temperature = lm35.getTemperature();


  // Exibir a temperatura no monitor serial
  Serial.print("Temperatura: ");
  Serial.print(temperature);
  Serial.println(" °C");


  // Aguardar 1 segundo antes de fazer outra leitura
  delay(1000);
}
```

## Dinâmica Pair Teaching

### Como Fazer?

1. Faça par com um colega do seu grupo;
2. Caso o grupo tenha número ímpar de aluno, um grupo terá 3 integrantes;
3. Uma pessoa faz o papel de instrutor e a outra o papel de aluno por 15 minutos.
4. Após esse tempo, inverta os papéis.
5. A dupla deverá explicar à turma o que aprendeu sobre classes, funções ou métodos e trazer um exemplo diferente dos exemplos do professor.

### Premiação

As 5 melhores duplas ganharão um prêmio. Haverá uma votação.
