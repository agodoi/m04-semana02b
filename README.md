# Atendimento do Professor

## Terças e quintas. Professor de horário parcial. Nesses 2 dias, podem contar comigo!

# Semana 02B - Programação

Revisão de fluxo de controle e funções, com introdução à Programação Orientada a Objetos em C++, utilizando o framework Arduino. Desenvolvimento de um exemplo de pisca-pisca com classes e simulação no Wokwi.

Adoção do VSCode + Wokwi + Platformio como ambiente de programação. Seguir [esses passos](https://docs.google.com/document/d/1etH9pohtJPUVs3hmWygYFLzkBLV8PzsorxjhviC-04g/edit?usp=sharing)


## Vantagens para o seu projeto da Estapar

* Classes permitem reunir os dados e as ações de cada componente do projeto;
* Favorecem a organização, a reutilização e a manutenção do código;
* Permitem criar objetos independentes a partir de uma mesma classe, como dois LEDs com intervalos diferentes;
* O uso de classes não garante, por si só, execução mais rápida ou menor consumo de memória. Esses resultados dependem da implementação.

### Ambiente do VS Code

Usar o VS Code com as extensões do Wokwi e PlatformIO para simular circuitos Arduino oferece uma experiência mais profissional, integrada e próxima do ambiente real de desenvolvimento embarcado. 

O VS Code permite escrever, compilar e depurar o código em um único local, com autocompletar inteligente, controle de versões (Git/GitHub) e suporte direto a bibliotecas externas. 

O PlatformIO facilita a configuração de múltiplas placas e ambientes (ESP32, Arduino UNO, etc.), além de gerar arquivos de **build** consistentes e permitir testes locais. 

Já o Wokwi integrado ao VS Code adiciona a simulação visual do circuito, mas com maior controle sobre o código-fonte, dependências e integração com hardware físico, algo limitado na versão web, que é mais voltada a demonstrações rápidas e possui restrições de bibliotecas, conectividade e armazenamento local.

Seguir [esses passos](https://docs.google.com/document/d/1etH9pohtJPUVs3hmWygYFLzkBLV8PzsorxjhviC-04g/edit?usp=sharing) para montar o seu setup.

Vamos gravar um Pisca-pisca no seu ESP32 como exemplo.

#### Cuidados

* **Verificar o arquivo platformio.ini** — certifique-se de que o ambiente, a placa e o framework estão corretamente definidos para evitar erros de compilação. É nesse arquivo que você deve adicionar as bibliotecas dos sensores, caso necessite. O GPeTo pode te ajudar a criar esse arquivo pedindo para ele adicionar o sensor X;
* Sincronizar as versões das bibliotecas — use sempre versões compatíveis entre o VS Code, PlatformIO e o simulador Wokwi para evitar conflitos de dependência.

### CLP Conceitos

**O que é um CLP?**

Um Controlador Lógico Programável (CLP) é um equipamento usado no controle de máquinas e processos industriais. Ele lê sinais de entrada, executa um programa e comanda saídas, que podem acionar dispositivos por meio de interfaces apropriadas.

Assim como uma placa com ESP32, um CLP pode executar uma lógica de controle. Entretanto, os CLPs são projetados para aplicações industriais, com características de alimentação, proteção elétrica, conexões e imunidade a interferências adequadas às condições especificadas pelo fabricante. Suas saídas podem ser a relé, transistor ou de outros tipos, conforme o modelo.

Um CLP convencional não deve ser confundido com um CLP de segurança. A robustez industrial não significa que qualquer CLP possa executar funções de segurança ou continuar funcionando durante uma queda de energia.

Nesse momento, você só precisa saber que existe esse equipamento, porque mais para frente, quem for fazer Engenharia da Computação, terá um estudo mais aprofundado.

A figura abaixo, mostra um CLP profissional, com vários módulos de interface e várias entradas e saídas de dados.

<img src="https://github.com/agodoi/m04-semana02b/blob/main/imgs/clp01.png" width="500">

O CLP a seguir, é um dos mais baratos e simples de se programar.

<img src="https://github.com/agodoi/m04-semana02b/blob/main/imgs/clp02.png" width="500">

### Ciclo de Varredura

No modelo básico de execução cíclica, o CLP lê as entradas, executa o programa e atualiza as saídas. Essa repetição pode ser comparada, de forma introdutória, à execução contínua de `loop()` no framework Arduino, embora os mecanismos de atualização das entradas e saídas sejam diferentes.

A ordem de execução das instruções pode influenciar o resultado. Se uma mesma variável ou saída receber várias atribuições durante uma execução sequencial, a última atribuição executada pode determinar seu valor final. Isso não significa que as últimas linhas sejam mais importantes ou tenham prioridade de segurança.

A parada de emergência deve utilizar uma arquitetura de segurança adequada à máquina, definida a partir da avaliação de riscos, podendo envolver relé de segurança ou CLP de segurança e dispositivos apropriados. Colocar uma condição nas últimas linhas do programa de um CLP convencional não garante uma parada de emergência segura.

Veja o fluxograma do ciclo básico de varredura:

### CLP - Definições Básicas

Conforme o modelo e os módulos instalados, um CLP pode possuir entradas e saídas digitais e analógicas. Entre os sinais analógicos industriais, são comuns os de corrente de 4 a 20 mA e os de tensão de 0 a 10 V. Cada sinal exige uma interface compatível.

Os sinais digitais representam estados lógicos, como ligado e desligado. Em muitos CLPs, as entradas digitais utilizam 24 V em corrente contínua. Portanto, compartilhar os conceitos de HIGH e LOW não significa que os sinais possam ser conectados diretamente aos GPIOs de uma placa com ESP32.

<img src="https://github.com/agodoi/m04-semana02b/blob/main/imgs/varreduraCLP.png" width="200">

<img src="https://github.com/agodoi/m04-semana02b/blob/main/imgs/clp04.png" width="500">


### Conclusões parciais

#### Como ficaria seu ESP32 se ele fosse um CLP?

<img src="https://github.com/agodoi/m04-semana02b/blob/main/imgs/clp03.png" width="500">

---

## Linguagem C++ no Arduino - Classes, Métodos e Atributos

### Classes
Uma classe define um tipo de dado que pode reunir atributos e métodos. Os atributos armazenam dados, e os métodos representam operações associadas a esse tipo.

Um objeto é uma instância de uma classe. Por exemplo, em `Blinker led(23, 500);`, `Blinker` é a classe e `led` é o objeto criado a partir dela.

Nesta aula, utilizaremos Programação Orientada a Objetos (POO) em C++, com o framework Arduino. A linguagem C não possui os recursos de classes apresentados nestes exemplos.

### Componentes de uma Classe
- **Atributos:** Dados associados ao objeto, como o pino do LED, o intervalo e seu estado atual.
- **Métodos:** Funções que definem operações, como atualizar o estado do LED ou obter uma temperatura.
- **Construtor:** Rotina especial executada na criação do objeto, utilizada para inicializá-lo.

Atributos e métodos são membros da classe.

Ao criar uma classe, você define como o objeto será inicializado, como as propriedades podem ser acessadas e modificadas, e quais métodos estarão disponíveis para interagir com o objeto. Isso facilita a criação de programas mais extensíveis e de fácil manutenção.

### Exemplo Prático 1 - Pisca-pisca usando Classe

```cpp
#include <Arduino.h>

class Blinker {
  private:
    int _pino;
    unsigned long _intervalo;
    unsigned long _previousMillis;
    bool _state;

  public:
    Blinker(int pin, unsigned long interval) {
      _pino = pin;
      _intervalo = interval;
      _previousMillis = 0;
      _state = false;
    }

    void begin() {
      pinMode(_pino, OUTPUT);
      digitalWrite(_pino, LOW);
      _previousMillis = millis();
    }

    void update() {
      unsigned long currentMillis = millis();

      if (currentMillis - _previousMillis >= _intervalo) {
        _previousMillis = currentMillis;
        _state = !_state;
        digitalWrite(_pino, _state ? HIGH : LOW);
      }
    }
};

// Exemplo para uma placa ESP32 com GPIO 23 disponível.
// Conecte um LED externo com resistor limitador de corrente.
Blinker led(23, 500);

void setup() {
  led.begin();
}

void loop() {
  led.update();
}
```
    
O construtor inicializa os atributos do objeto. O método `begin()`, chamado em `setup()`, configura o hardware após a inicialização do framework Arduino.

O método `update()` alterna o estado do LED a cada 500 ms, sem utilizar `delay()`. Assim, um ciclo completo de acender e apagar dura aproximadamente 1 segundo.
---

### Exemplo Prático 2 - Lendo sensor de temperatura usando Classe

Este exemplo utiliza um Arduino Uno R3 com um sensor LM35 conectado à entrada A0. Nessa configuração, `analogRead()` retorna valores de 0 a 1023. A conversão abaixo considera uma referência nominal de 5 V; a tensão real de referência influencia a precisão da medição.

O LM35 fornece uma variação de 10 mV por grau Celsius, sem o deslocamento de 500 mV característico do TMP36. O código não deve ser transferido diretamente para um ESP32 sem adaptar o pino e a conversão do ADC.

```cpp
#include <Arduino.h>

class TemperatureSensor {
  private:
    int _pino;

  public:
    TemperatureSensor(int pin) {
      _pino = pin;
    }

    float getTemperature() {
      int sensorValue = analogRead(_pino);

      // Conversão aproximada para Uno R3 com referência de 5 V.
      float voltage = sensorValue * (5.0 / 1023.0);

      // LM35: 10 mV por grau Celsius.
      float temperature = voltage * 100.0;

      return temperature;
    }
};

TemperatureSensor lm35(A0);

void setup() {
  Serial.begin(9600);
}

void loop() {
  float temperature = lm35.getTemperature();

  Serial.print("Temperatura: ");
  Serial.print(temperature);
  Serial.println(" °C");

  delay(1000);
}
```

### Passos para criar uma classe

**1)** Comece digitando ```class``` + nome que desejar e abra uma chave geral {

**2)** Digite `private:` e declare os atributos que serão acessados pelos métodos da própria classe. No uso apresentado nesta aula, o código externo não poderá acessar esses atributos diretamente. O prefixo `_`, como em `_pino`, é apenas uma convenção de nomenclatura; quem determina o acesso privado é `private:`.

**3)** Digite ```public:```. Nessa área, vamos criar o construtor e as **ações** da classe. Exemplos: testar botão, acender led, coletar sensor, formatar um número, realizar um cálculo, calcular um tempo, etc. E nessas ações, você vai usar as variáveis que foram declaradas no ```private```;

**3.1)** Na seção `public:`, declare o construtor. Ele possui o mesmo nome da classe e não declara um tipo de retorno. Nos exemplos desta aula, o construtor recebe parâmetros e utiliza seus valores para inicializar os atributos do objeto.

Para configurar o hardware, utilizaremos um método `begin()`, chamado em `setup()`. Isso evita depender da disponibilidade do hardware durante a construção de objetos globais.

Exemplo:

```cpp
public:
  Blinker(int pin, unsigned long interval) {
    _pino = pin;
    _intervalo = interval;
    _previousMillis = 0;
    _state = false;
  }

  void begin() {
    pinMode(_pino, OUTPUT);
    digitalWrite(_pino, LOW);
    _previousMillis = millis();
  }
```

**3.2)** Após o construtor, declare os métodos da classe. Nos exemplos abaixo, cada método apresenta um tipo de retorno, um nome, parênteses com os parâmetros, quando houver, e um corpo entre chaves.

O método `getTemperature()` retorna um valor do tipo `float`:

```cpp
float getTemperature() {
  int sensorValue = analogRead(_pino);
  float voltage = sensorValue * (5.0 / 1023.0);
  float temperature = voltage * 100.0;

  return temperature;
}
```

Esse cálculo considera o Arduino Uno R3 com referência nominal de 5 V e um sensor LM35.

Para chamar o método público de um objeto, utilizamos o operador ponto:

```cpp
float temperatura = lm35.getTemperature();
```

Nessa expressão, `lm35` é o objeto e `getTemperature()` é o método chamado. O ponto acessa um membro do objeto; ele não concatena nomes ou textos.

Já o método `update()` realiza uma ação e não retorna um valor:

```cpp
void update() {
  unsigned long currentMillis = millis();

  if (currentMillis - _previousMillis >= _intervalo) {
    _previousMillis = currentMillis;
    _state = !_state;
    digitalWrite(_pino, _state ? HIGH : LOW);
  }
}
```

**ATENÇÃO:** `float` indica que o método retorna um valor desse tipo. Já `void` indica que o método não retorna um valor.

Um método `void` pode utilizar `return;`, sem uma expressão, para encerrar sua execução antecipadamente. Portanto, `void` não significa ausência obrigatória da instrução `return`.

**4)** Encerre a sua função (método) fechando a chave

**5)** Encerre a classe colocando uma };


## Dinâmica Pair Teaching

<img src="https://github.com/agodoi/m04-semana02b/blob/main/imgs/pairteaching.png" width="500">

### Como Fazer?

1. Faça par com um colega do seu grupo;
2. Caso o grupo tenha número ímpar de aluno, um grupo terá 3 integrantes;
3. Uma pessoa faz o papel de instrutor e a outra o papel de aluno por 15 minutos.
4. Após esse tempo, inverta os papéis.
5. A dupla deverá explicar à turma o que aprendeu sobre classes, funções ou métodos e trazer um exemplo diferente dos exemplos do professor.
6. Vamos sortear 5 duplas para vir aqui na frente explicar;

### Premiação

As 5 melhores duplas ganharão um prêmio se explicar bem.
