Como dou aula de robotica, aproveitei o desafio para criar uma aula de **Robótica de Combate (Sumô/Destruição)**.
Esta é uma excelente forma de ensinar lógica de controle e condicionais de forma prática e empolgante.

---

## 🤖 Plano de Aula: Construindo um Robô de Combate

**Objetivo:** Integrar controle manual (botões) com automação sensorial (sensor ultrassônico) para criar um robô capaz de se movimentar e atacar autonomamente.

### 1. Lista de Materiais

Para este projeto, cada grupo de alunos precisará de:

* **Microcontrolador:** 1x Arduino Uno (ou Nano).
* **Chassi:** Kit chassi 2WD (2 rodas + roda boba).
* **Driver de Motor:** 1x Ponte H L298N (para controlar os motores de locomoção).
* **Motores de Locomoção:** 2x Motores DC 6V com redução.
* **Motor da Serra:** 1x Motor DC de alta rotação + 1x Transistor (TIP120) ou Módulo Relé.
* **Sensor:** 1x Sensor Ultrassônico HC-SR04.
* **Controle:** 4x Push-buttons + Resistores de 10k$\Omega$ (para pull-down).
* **Alimentação:** Suporte para 4 pilhas AA ou Bateria LiPo 7.4V.
* **Diversos:** Protoboard, Jumpers e uma "serra" simbólica (disco de papelão ou plástico).

---

### 2. O Conceito Lógico

O robô operará em modo híbrido:

1. **Movimentação:** Obedece aos comandos dos botões.
2. **Segurança/Ataque:** O sensor "varre" a frente. Se algo entrar no raio de 15 cm, a serra liga automaticamente, independente do movimento.

---

### 3. Código Comentado (C++)

Abaixo, o código estruturado para facilitar o entendimento dos alunos sobre funções e leitura de sensores.

```cpp
// Definição dos Pinos
#define motorEsq 5
#define motorDir 6
#define motorSerra 9
#define trigPin 10
#define echoPin 11

// Pinos dos Botões
#define btnFrente 2
#define btnTras 3
#define btnEsq 4
#define btnDir 7

void setup() {
  pinMode(motorEsq, OUTPUT);
  pinMode(motorDir, OUTPUT);
  pinMode(motorSerra, OUTPUT);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  
  pinMode(btnFrente, INPUT);
  pinMode(btnTras, INPUT);
  pinMode(btnEsq, INPUT);
  pinMode(btnDir, INPUT);
  
  Serial.begin(9600);
}

void loop() {
  long duracao;
  int distancia;

  // Lógica do Sensor Ultrassônico
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  duracao = pulseIn(echoPin, HIGH);
  distancia = duracao * 0.034 / 2; // Cálculo para converter em cm

  // Controle da Serra (Autônomo)
  if (distancia > 0 && distancia <= 15) {
    digitalWrite(motorSerra, HIGH);
  } else {
    digitalWrite(motorSerra, LOW);
  }

  // Lógica de Movimentação (Manual)
  if (digitalRead(btnFrente) == HIGH) {
    mover(HIGH, HIGH); // Frente
  } else if (digitalRead(btnTras) == HIGH) {
    mover(LOW, LOW);   // Trás (invertendo a polaridade se necessário)
  } else if (digitalRead(btnEsq) == HIGH) {
    digitalWrite(motorEsq, LOW);
    digitalWrite(motorDir, HIGH);
  } else if (digitalRead(btnDir) == HIGH) {
    digitalWrite(motorEsq, HIGH);
    digitalWrite(motorDir, LOW);
  } else {
    parar();
  }
}

// Função Auxiliar para Movimento
void mover(int estadoE, int estadoD) {
  digitalWrite(motorEsq, estadoE);
  digitalWrite(motorDir, estadoD);
}

void parar() {
  digitalWrite(motorEsq, LOW);
  digitalWrite(motorDir, LOW);
}

```

---

### 4. Roteiro da Aula (4 Passos)

1. **Explicação do Sensor ():** Explique por que dividimos o tempo por 2 (o som vai e volta).
2. **Montagem da Ponte H:** Mostre como a Ponte H permite que o Arduino controle motores que precisam de mais corrente do que ele pode fornecer.
3. **Lógica de Condicionais:** Discuta com os alunos por que a serra deve ter prioridade no código ou rodar paralelamente à leitura dos botões.
4. **O Desafio:** Coloque os robôs em uma arena. O objetivo é conseguir tocar o oponente com a serra ativa enquanto desvia dos ataques.

---

### Dica de Ouro para o Professor:

Peça para os alunos observarem que, se pressionarem dois botões ao mesmo tempo, o código atual prioriza o que vem primeiro no `if/else`. Um desafio extra seria programar para que dois botões pressionados resultem em um movimento diagonal ou curva suave!
