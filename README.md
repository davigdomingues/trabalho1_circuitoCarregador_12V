# Projeto de Carregador de Celular (3 a 12 V)

## Integrantes do Grupo

* **Davi Gabriel Domingues** – Nº USP: 15447497
* **Christyan Paniago Nantes** – Nº USP: 15635906
* **Giovanna Nascimento Noventa** – Nº USP: 15637210

---

## Objetivos do Projeto

Este trabalho tem como objetivo projetar, descrever e simular uma fonte retificadora ajustável que converta corrente alternada (CA) de 127 V (valor eficaz) e frequência de 60 Hz em corrente contínua (CC), com saída regulável na faixa de **3 a 12 V**. A fonte deve ser adequada para aplicações práticas, como o carregamento de celulares e pequenos dispositivos eletrônicos.

Além da simulação funcional do circuito, o projeto visa aplicar conhecimentos de eletrônica analógica, tais como:

* Retificação de tensão
* Filtragem e controle de ripple
* Regulação de tensão
* Polarização de transistores
* Dissipação de energia
* Proteção de carga

---

## Descrição Geral do Circuito

O circuito foi desenvolvido no simulador **Falstad** para testar dinamicamente os componentes e verificar a resposta em tempo real.

**Topologia do circuito**:

1. Transformador rebaixador (127 V CA → 3–12 V CC) e isolamento galvânico
2. Ponte retificadora de onda completa (4 × 1N4007)
3. Capacitor de filtro (≥ 470 µF) para redução de ripple
4. Transistor NPN (BC547 ou 2N2222) para regulação de saída
5. Potenciômetro (10 kΩ) para ajuste de tensão de saída
6. Diodo Zener (12 V / 1 W) para limitação de tensão máxima
7. LED indicador de operação
8. Resistor de carga para proteção e descarga do capacitor

**Imagens do circuito**:

**I) Falstad:**

![Circuito carregador 12V Falstad](Imagens/Circuito%20falstad.png)

**II) Circuito físico implementado:**


**III) Esquema do PCB (Eagle)**:

![Circuito carregador 12V Falstad](Imagens/Esquemático%20PCB%20(Eagle).png)

![Circuito carregador 12V Falstad](Imagens/PCB%20Eagle.png)

![Circuito carregador 12V Falstad](Imagens/PCB%20Eagle%20(detalhado).png)


**Links úteis**:

* Simulação interativa no Falstad: [https://tinyurl.com/27o6eqhh](https://tinyurl.com/27o6eqhh)
* Vídeo de execução do circuito: [https://youtu.be/P82pu6Qgv4M](https://youtu.be/P82pu6Qgv4M)

---

## Explicação Técnica (Geral)

1. **Fonte de Corrente Alternada (CA) e Transformador**

   A entrada do circuito consiste em uma fonte senoidal padrão da rede elétrica brasileira, com tensão eficaz de 127 V e frequência de 60 Hz. A tensão de pico é dada por:

   ```
   V_pico = V_rms * sqrt(2)
   ```

   Essa fonte está conectada a um transformador rebaixador, que tem a função de reduzir a tensão para valores apropriados ao carregamento (entre 3V e 12V, ajustáveis). O transformador também realiza o isolamento galvânico entre a rede elétrica e o circuito de carga, garantindo maior segurança. A relação de espiras (N₁\:N₂) determina o valor da tensão de saída no enrolamento secundário, de acordo com:

   ```
   N1/N2 = V1/V2
   ```

   Nesse caso, o ‘secundário’ representa a saída, enquanto ‘primário’ representa a entrada. Tem-se a imagem a seguir das especificações dos transformadores presentes para o circuito:

   Para este projeto, foi utilizado o transformador número 1.

2. **Ponte Retificadora de Diodos (Retificador de Onda Completa)**

   A ponte retificadora é composta por quatro diodos de silício (ex.: 1N4007) dispostos em configuração clássica de onda completa. Essa topologia converte a corrente alternada do transformador em tensão contínua pulsante, mantendo a polaridade constante nos terminais de saída. Ambas as partes do ciclo da CA são aproveitadas, aumentando a eficiência e a continuidade do fluxo de carga. A tensão de saída ainda possui ondulações (ripple), que são suavizadas por um capacitor.

3. **Capacitor Eletrolítico de Filtro (≥ 470 µF)**

   Responsável pela filtragem da tensão pulsante gerada pela ponte de diodos, o capacitor atua como um banco de carga: armazena energia durante os picos de tensão e a libera nos vales, suavizando as oscilações. O valor mínimo, para esse projeto, que pode ser adotado é de 470 µF, o suficiente para manter o ripple abaixo de 10%, com base na expressão:

   ```
   C >= I_carga / (2 * f * V_ripple)
   ```

4. **Resistor de Carga**

   O resistor limita a corrente de saída e dissipa energia em forma de calor, protegendo os componentes sensíveis como o LED e o transistor contra sobrecorrentes. Além disso, auxilia no controle da velocidade de descarga do capacitor, estabilizando a resposta do circuito frente a variações rápidas de carga.

5. **Transistor NPN (BJT)**

   O transistor NPN (ex.: BC547 ou 2N2222) funciona como chave de controle ou amplificador de corrente. A condução ocorre quando a base recebe tensão suficiente (tipicamente ≥ 0.7 V), permitindo a passagem de corrente do coletor ao emissor. No circuito, o transistor colabora com o controle de tensão de saída, regulando o fornecimento de energia ao LED e à carga em conjunto com o potenciômetro.

6. **Potenciômetro**

   Um resistor variável, de valor típico 10 kΩ, que permite ajustar a tensão de saída do carregador. Atua diretamente sobre a polarização da base do transistor, controlando sua região de operação. Com isso, é possível definir a tensão final entregue ao dispositivo a ser carregado, variando de forma segura entre 3V a 12V.

7. **LED (Diodo Emissor de Luz)**

   O LED serve como indicador visual de funcionamento do circuito. Quando há condução de corrente suficiente, o LED acende, indicando que o circuito está operando corretamente e fornecendo tensão à carga. Sua intensidade luminosa depende da corrente que o atravessa.

8. **Diodo Zener (Regulador de Tensão)**

   O diodo Zener (12 V / 1 W) é responsável por limitar a tensão máxima do circuito. Ele entra em condução quando a tensão atinge seu valor de ruptura em polarização reversa, impedindo que ultrapasse 12 V, protegendo assim os demais componentes e o dispositivo carregado. Atua como regulador passivo de tensão.

9. **Terra (GND)**

   Adicionado na simulação por conveniência visual, não interfere diretamente na funcionalidade elétrica do circuito. Serve como referência de potencial comum e facilita a organização esquemática no ambiente de simulação.

## Componentes e Funções (explicação resumida)

| Componente                        | Função                                               |
| --------------------------------- | ---------------------------------------------------- |
| Transformador rebaixador          | Reduz 127 V CA para 3–12 V CC e isola galvanicamente |
| Ponte retificadora (1N4007 × 4)   | Converte CA em CC pulsante (onda completa)           |
| Capacitor eletrolítico (≥ 470 µF) | Suaviza ondulações, mantendo ripple abaixo de 10%    |
| Transistor NPN (BC547 / 2N2222)   | Regula corrente e tensão de saída                    |
| Potenciômetro (10 kΩ)             | Ajusta polarização da base do transistor             |
| Diodo Zener (12 V / 1 W)          | Limita tensão máxima a 12 V                          |
| LED indicador                     | Indica o funcionamento correto do circuito           |
| Resistor de carga                 | Limita corrente e estabiliza descarga do capacitor   |
| GND                               | Referência de potencial comum (organização visual)   |

---

## Funcionamento Resumido

1. A tensão CA de 127 V é reduzida pelo transformador.
2. A ponte de diodos retifica a tensão em CC pulsante.
3. O capacitor de filtro reduz o ripple.
4. O potenciômetro regula a base do transistor, ajustando a saída.
5. O LED sinaliza a presença de tensão na carga.
6. O Zener protege contra sobretensão acima de 12 V.

---

## Lista de Materiais e Custos

| Código | Descrição                                  | Qtde | Valor Unit. (R\$) | Valor Total (R\$) |
| ------ | ------------------------------------------ | ---: | ----------------: | ----------------: |
| 102927 | Transistor BC337-40 (50 V / 0,8 A) – TO-92 |    1 |              0,70 |              0,70 |
| 102579 | Jumper Macho × Macho (kit 10 pcs)          |    1 |              7,00 |              7,00 |
| 106876 | Protoboard 400 pinos                       |    1 |             21,70 |             21,70 |
| 118210 | Capacitor ELCO 1000 µF × 35 V              |    1 |              2,00 |              2,00 |
| 106665 | Diodo Zener 13 V / 1 W (1N4743)            |    1 |              0,50 |              0,50 |
| 101973 | Diodo retificador 1N4007                   |    5 |              0,20 |              1,00 |
| 102048 | LED 5 mm difuso                            |    1 |              0,50 |              0,50 |
| 102996 | Potenciômetro 1 W B10K                     |    1 |              7,00 |              7,00 |
| 102269 | Resistor 2,2 kΩ                            |    2 |              0,07 |              0,14 |
| 102043 | Resistor 1 kΩ                              |    2 |              0,07 |              0,14 |
| 102281 | Resistor 470 Ω                             |    2 |              0,07 |              0,14 |
| 103464 | Resistor 100 Ω                             |    2 |              0,07 |              0,14 |
|        | **Total Geral**                            |      |                   |         **43,20** |
