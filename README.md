# Controle de Sinais de Trânsito com Inclusão para Deficientes Visuais

Este repositório contém o código e as instruções para a implementação de um sistema de controle de sinais de trânsito utilizando um Raspberry Pi Pico, com funcionalidades voltadas para auxiliar deficientes visuais na travessia de cruzamentos. O projeto foi desenvolvido em linguagem C e simulado no **Wokwi**.

## ⚡ Objetivo

Desenvolver um sistema de baixo custo que controle os sinais de trânsito de carros e pedestres, incluindo:

- Um sinal sonoro para indicar aos pedestres quando é seguro atravessar.
- Um botão de acionamento que fecha o sinal de trânsito para carros e libera a travessia para pedestres.

## 🔧 Componentes Utilizados

### Hardware

- **Raspberry Pi Pico**
- LEDs:
  - Vermelho, amarelo e verde para o semáforo de carros
  - Verde para o semáforo de pedestres
- **Buzzer:** para emitir sons
- **Push Button:** para simular a botoeira do pedestre
- **Resistores:** para limitar a corrente nos LEDs
- Protoboard e fios

### Software

- Linguagem: **C**
- Simulação no [Wokwi](https://wokwi.com/)

## 🔄 Funcionamento

### Estado Inicial

- O semáforo dos carros alterna automaticamente entre as cores:
  - **Verde:** 8 segundos
  - **Amarelo:** 2 segundos
  - **Vermelho:** 10 segundos
- O LED verde para pedestres está apagado e o buzzer desativado.

### Quando o Botão é Pressionado

1. O semáforo dos carros:
   - Aciona o LED amarelo por 5 segundos.
   - Em seguida, aciona o LED vermelho por 15 segundos.
2. O LED verde para pedestres é ligado durante os 15 segundos em que o LED vermelho dos carros está ativo.
3. O buzzer emite sons intermitentes durante o período de travessia segura.

### Retorno ao Estado Inicial

- O semáforo dos carros volta a alternar normalmente.
- O LED verde dos pedestres e o buzzer são desligados.

## 📊 Diagrama de Conexões

- **Semáforo de Carros:**
  - LED verde conectado ao GPIO 2
  - LED amarelo conectado ao GPIO 3
  - LED vermelho conectado ao GPIO 4
- **Semáforo de Pedestres:**
  - LED verde conectado ao GPIO 5
- **Buzzer:** conectado ao GPIO 7
- **Push Button:** conectado ao GPIO 6 (com pull-up interno)

## 🗒 Estrutura do Código

O código está dividido em funções para simplificar o controle:

- `inicializar_pinos()`: Configura os pinos do Raspberry Pi Pico.
- `alternar_sinal_carros()`: Controla o funcionamento automático do semáforo dos carros.
- `sinal_pedestre()`: Gerencia o comportamento do sistema quando o botão é pressionado.

## 🔼 Simulação no Wokwi

Para simular o projeto:

1. Acesse o [Wokwi](https://wokwi.com/).
2. Monte o circuito seguindo o diagrama de conexões.
3. Copie e cole o código em C na interface do Wokwi.
4. Execute a simulação e teste o funcionamento do botão e dos sinais.

## 🌐 Como Executar no Raspberry Pi Pico

1. Instale o **SDK do Raspberry Pi Pico** no seu ambiente.
2. Compile o código para gerar um arquivo `.uf2`.
3. Conecte o Raspberry Pi Pico ao computador em modo de bootloader.
4. Arraste o arquivo `.uf2` para a unidade do Pico.
5. Conecte os componentes ao Pico conforme o diagrama e teste o sistema.

## 🚀 Melhorias Futuras

- Adicionar sensores de aproximação para detectar pedestres.
- Implementar controle remoto via Bluetooth.
- Expandir o projeto para sincronização em múltiplos cruzamentos.

