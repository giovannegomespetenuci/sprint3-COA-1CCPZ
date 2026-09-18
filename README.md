# Sistema Inteligente de Controle de Sessão de Recarga (Veículos Elétricos)

Projeto desenvolvido para a Sprint 3 da disciplina de **Computer Organization and Architecture (COA)**. O projeto consiste em um sistema baseado no Raspberry Pi Pico (RP2040) inspirado no conceito do *GoodWe Smart Energy Controller*, que gerencia a recarga de um veículo elétrico com base na energia disponível (Geração de energia vs. Consumo da residência).

## Integrantes do Projeto

*   **Alan Junio Araujo de Souza** - RM 574112
*   **Arthur Vettorazzo de Souza** – RM 569445
*   **Brayan Barbosa Dos Santos** - RM 573682
*   **Giovanne Gomes Petenuci** - RM 574091
*   **Gustavo Zibini Belizario** - RM 561376
*   **Luiz Otávio Brito Freixo** - RM 569977

## Links Importantes

*   **Apresentação e Demonstração:** [Assista ao vídeo do projeto no YouTube](https://www.youtube.com/watch?v=8P1V_j2c_ig)

## Como Executar

Para testar o projeto, não é necessário instalar nenhuma IDE ou configurar o hardware fisicamente. **Basta copiar o link do simulador na internet (fornecido pelo grupo) no seu navegador que o projeto já abrirá pronto para rodar.** A simulação iniciará automaticamente o display e carregará a interface gráfica.

## Como o Código Funciona

O código foi programado em MicroPython para o microcontrolador Raspberry Pi Pico (RP2040) e é dividido em blocos principais:

1.  **Mapeamento de Hardware:** Configura as saídas digitais para os LEDs físicos (Verde, Amarelo e Vermelho) e os barramentos de comunicação: `SPI0` para o Display Gráfico (ILI9341) e `I2C0` para o sensor de toque (Touch FT6206).
2.  **Interface Gráfica (Display e Touch):** Cria drivers e funções de desenho para renderizar a interface no display (textos, botões, painéis e cores em formato RGB565). Ele também captura os toques na tela para interação com o usuário.
3.  **Lógica de Controle de Energia:** 
    *   O sistema calcula a **Energia Disponível** subtraindo o *Consumo* da *Geração*.
    *   **Recarga Autorizada (LED Verde):** Se houver 1000W ou mais disponíveis.
    *   **Recarga Reduzida (LED Amarelo):** Se houver energia disponível, mas for menor que 1000W.
    *   **Recarga Bloqueada (LED Vermelho):** Se não houver energia disponível (0 ou negativo).
4.  **Bases Numéricas (Conceito de Arquitetura):** O código pega o valor da "Energia Disponível" na base decimal e faz a conversão em tempo real, exibindo também seu correspondente em **Hexadecimal (HEX)** e **Binário (BIN)** de 16 bits na tela do display e no console serial.
5.  **Interação do Usuário:** Dentro de um loop infinito (`while True`), o sistema monitora toques na tela. O usuário pode alternar entre 3 "Cenários" pré-programados de geração/consumo ou usar os botões manuais de "+500" e "-500" na geração. Sempre que ocorre uma alteração, a interface, os cálculos e os LEDs são atualizados instantaneamente.
