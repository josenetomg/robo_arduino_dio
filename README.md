# Robô de Combate Automatizado com Arduino (Sumô / Destruição)

<p align="center">
  <img src="https://img.shields.io/badge/Projeto-DIO_LAB-orange?style=for-the-badge" alt="DIO LAB Project">
  <img src="https://img.shields.io/badge/Hardware-Arduino-blue?style=for-the-badge" alt="Arduino">
  <img src="https://img.shields.io/badge/Categoria-Robótica_e_Embarcados-green?style=for-the-badge" alt="Robotics">
</p>

## 📌 Sobre o Projeto

Este repositório contém o código-fonte e as especificações de hardware desenvolvidos para o desafio prático **"Programando um Robô do Zero com Arduino"** pela **Digital Innovation One (DIO)**. 

O projeto consiste na arquitetura e programação de um robô móvel com tração diferencial, operável por controle manual via botões e equipado com um sistema autônomo de resposta a ameaças (arma de destruição por proximidade), simulando o comportamento de um robô de combate de arena.

---

## ⚙️ Requisitos Funcionais e Arquitetura

O sistema robótico foi projetado para executar duas dinâmicas principais: **Movimentação Direcional Manual** e **Combate Automatizado por Sensor**.

### 1. Sistema de Tração e Locomoção
*   **Configuração Cinematica:** Tração Diferencial baseada em dois motores independentes:
    *   **Motor Esquerdo:** Responsável pela propulsão e curvas para o lado esquerdo.
    *   **Motor Direito:** Responsável pela propulsão e curvas para o lado direito.
*   **Interface de Controle (Inputs):** Matriz de 4 botões de pressão (push-buttons) mapeados para as seguintes funções de navegação:
    *   **Botão Frente:** Aciona ambos os motores no sentido horário.
    *   **Botão Trás:** Aciona ambos os motores no sentido anti-horário.
    *   **Botão Esquerda:** Inverte os sentidos/velocidades relativas dos motores para girar sobre o próprio eixo para a esquerda.
    *   **Botão Direita:** Inverte os sentidos/velocidades relativas dos motores para girar sobre o próprio eixo para a direita.

### 2. Módulo de Combate Autônomo
*   **Detecção de Alvos:** Utilização de um sensor de proximidade (ex: Ultrassônico HC-SR04 ou Infravermelho).
*   **Lógica de Atuação:** Monitoramento contínuo da distância até o oponente.
*   **Gatilho de Defesa:** Sempre que a distância lida for **igual ou inferior a 15 cm ($\le 15\text{ cm}$)**, o microcontrolador envia um sinal lógico alto para ativar o atuador de destruição (motor dedicado à serra elétrica acoplada).

---

## 🛠️ Possíveis Componentes Utilizados (Hardware)

*   **Microcontrolador:** Arduino Uno (ou similar baseado no ATmega328P).
*   **Driver de Motor:** Ponte H (L298N ou L293D) para controle dos motores de tração DC.
*   **Sensores:** Sensor Ultrassônico HC-SR04 (ou sensor de distância Sharp IR).
*   **Atuador de Arma:** Relé ou Transistor MOSFET de potência para acionamento do motor da serra elétrica.
*   **Inputs:** 4 Push-buttons com resistores de pull-down/pull-up.

---

## 📂 Estrutura do Repositório

*   `/src`: Contém o arquivo principal com o código-fonte em C/C++ (`.ino`) para o Arduino.
*   `/schematics`: (Opcional) Diagramas de conexões elétricas e pinagem do circuito.

---

<p align="center">
  Desenvolvido com foco em lógica de programação para sistemas embarcados por <a href="https://github.com/josenetomg">José Joaquim Brandão Neto</a>.
</p>
