
### 🎯 O OBJETIVO

Construir e programar um robô controlado por botões que possua um **sistema de defesa automático**. 
O robô deve ser capaz de navegar pela arena e, ao detectar um oponente a menos de 15 cm, acionar sua serra (atuador) para o ataque.

---

### 🛠️ PARTE 1: O CIRCUITO (CHECKLIST)

Antes de ligar a bateria, verifique se todas as conexões estão firmes:

* [ ] **Motores de Tração:** Conectados às saídas OUT1/OUT2 e OUT3/OUT4 da Ponte H.
* [ ] **Alimentação:** O fio Vermelho (+) da bateria vai no "12V" da Ponte H; o Preto (-) vai no "GND".
* [ ] **União de Terras:** O GND da Ponte H está conectado ao GND do Arduino? (Obrigatório!).
* [ ] **Sensor Ultrassônico:** Posicionado na parte frontal, livre de obstáculos.
* [ ] **Botões:** Instalados com resistores de 10k$\Omega$ para evitar leituras falsas.

---

### 💻 PARTE 2: LÓGICA DE PROGRAMAÇÃO

Complete os blocos de lógica no seu código para que o robô responda corretamente:

1. **Cálculo da Distância:**


2. **Condicional de Ataque:**
```cpp
if (distancia <= 15) { 
    digitalWrite(motorSerra, HIGH); // Ligar Serra
} else {
    digitalWrite(motorSerra, LOW);  // Desligar Serra
}

```



---

### 🏁 PARTE 3: O DESAFIO NA ARENA

Após carregar o código, realize os testes de campo:

1. **Calibração de Movimento:** Se ao apertar "Frente" o robô girar em círculos, quais fios você deve inverter na Ponte H?
2. **Zona de Detecção:** Use uma régua para testar se a serra liga exatamente aos 15 cm.
3. **Manobrabilidade:** Tente fazer um "S" na arena sem tocar nas bordas.

---

### 🚀 BÔNUS (PARA QUEM TERMINAR CEDO)

**O Modo Recuo:** Modifique o código para que, se a distância for menor que **5 cm**, o robô pare de obedecer aos botões e dê ré automaticamente por 500ms antes de voltar ao controle manual. Isso evita colisões diretas que podem danificar o seu sensor!

---

**Dica do Assistente:** Mantenha os fios organizados com abraçadeiras. Um robô com "fios soltos" é um alvo fácil na arena de combate!

**Gostaria que eu explicasse como adicionar um "Modo Turbo" usando o PWM (analogWrite) para aumentar a velocidade do robô durante o ataque?**
