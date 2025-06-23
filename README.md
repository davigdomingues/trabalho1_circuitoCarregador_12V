# Projeto de Carregador de Celular (3 a 12 V)

> **Trabalho 1 - Projeto de Circuito Carregador de Celular de Tensão Ajustável**<br>
> **Disciplina**: SSC0180 - Eletrônica para Computação

## Integrantes do Grupo

* **Davi Gabriel Domingues** – Nº USP: 15447497
* **Christyan Paniago Nantes** – Nº USP: 15635906
* **Giovanna Nascimento Noventa** – Nº USP: 15637210

---

## Índice

1. [Objetivos do Projeto](#objetivos-do-projeto)
2. [Descrição Geral do Circuito](#descrição-geral-do-circuito)
   - [Topologia do circuito](#topologia-do-circuito)
   - [Imagens do circuito](#imagens-do-circuito)
   - [Links úteis](#links-úteis)
3. [Explicação Técnica (Geral)](#explicação-técnica-geral)
   - [Fonte de Corrente Alternada (CA) e Transformador](#fonte-de-corrente-alternada-ca-e-transformador)
   - [Ponte Retificadora de Diodos](#ponte-retificadora-de-diodos-retificador-de-onda-completa)
   - [Capacitor Eletrolítico de Filtro](#capacitor-eletrolítico-de-filtro-≥-348.77-µf)
   - [Resistor de Carga](#resistor-de-carga)
   - [Transistor NPN (BJT)](#transistor-npn-bjt)
   - [Potenciômetro](#potenciômetro)
   - [LED (Diodo Emissor de Luz)](#led-diodo-emissor-de-luz)
   - [Diodo Zener (Regulador de Tensão)](#diodo-zener-regulador-de-tensão)
   - [Terra (GND)](#terra-gnd)
   - [Escolhas de Projeto](#escolhas-de-projeto)
4. [Componentes e Funções (explicação resumida)](#componentes-e-funções-explicação-resumida)
5. [Funcionamento Resumido](#funcionamento-resumido)
6. [Lista de Materiais e Custos](#lista-de-materiais-e-custos)

---

## Objetivos do Projeto

Este trabalho tem como objetivo projetar, descrever e simular uma fonte retificadora ajustável que converta corrente alternada (CA) de 127 V (valor eficaz) e frequência de 60 Hz em corrente contínua (CC), com saída regulável na faixa de **3 a 12 V**, aproximadamente. A fonte deve ser adequada para aplicações práticas, como o carregamento de celulares e pequenos dispositivos eletrônicos.

Além da simulação funcional do circuito, o projeto visa aplicar conhecimentos de eletrônica analógica, tais como:

* Retificação de tensão
* Filtragem e controle de ripple
* Regulação de tensão
* Polarização de transistores
* Dissipação de energia
* Proteção de carga

---

## Descrição Geral do Circuito

O circuito foi desenvolvido no simulador **Falstad** para testar dinamicamente os componentes e verificar a resposta em tempo real, sendo, em seguida, montado, devidamente, o seu modelo físico associado.

**Topologia do circuito**:

1. Transformador rebaixador (127 V CA → 3–12 V CC) e isolamento galvânico
2. Ponte retificadora de onda completa (4 × 1N4007)
3. Capacitor de filtro (≥ 348.77 µF) para redução de ripple
4. Transistor NPN (BC547 ou 2N2222) para regulação de saída
5. Potenciômetro (10 kΩ) para ajuste de tensão de saída
6. Diodo Zener (12 V / 1 W) para limitação da tensão máxima
7. LED indicador de operação
8. Resistor de carga para proteção e descarga do capacitor

**Imagens do circuito**:

**I) Falstad:**

![Circuito carregador 12V Falstad](Imagens/Carregador//Falstad/Circuito%20falstad.png)

**II) Circuito físico implementado:**

![Circuito carregador 12V Modelo físico implementado (imagem 1)](Imagens/Carregador/Circuito%20físico/Imagem1.jpg)

![Circuito carregador 12V Modelo físico implementado (imagem 2)](Imagens/Carregador/Circuito%20físico/Imagem2.jpg)

![Circuito carregador 12V Modelo físico implementado (imagem 3)](Imagens/Carregador/Circuito%20físico/Imagem3.jpg)

![Circuito carregador 12V Modelo físico implementado (imagem 4)](Imagens/Carregador/Circuito%20físico/Imagem4.jpg)

![Circuito carregador 12V Modelo físico implementado (imagem 5)](Imagens/Carregador/Circuito%20físico/Imagem5.jpg)

![Circuito carregador 12V Modelo físico implementado (imagem 6)](Imagens/Carregador/Circuito%20físico/Imagem6.jpg)

**III) Esquema do PCB (Eagle)**:

![Esquemático do circuito carregador, feito na plataforma Eagle](Imagens/Eagle/Esquemático%20PCB%20(Eagle).png)

![Esquemático do PCB do circuito carregador, feito na plataforma Eagle](Imagens/Eagle/PCB%20Eagle.png)

![Esquemático das conexões do PCB do circuito carregador, feito na plataforma Eagle](Imagens/Eagle/PCB%20Eagle%20(detalhado).png)


**Links úteis**:

* Simulação interativa no Falstad: [https://tinyurl.com/27o6eqhh](https://tinyurl.com/27o6eqhh)
* Vídeo de execução do circuito: [https://youtu.be/P82pu6Qgv4M](https://youtu.be/P82pu6Qgv4M)
* Vídeo explicativo do circuito: [https://youtu.be/YhmCq-Fb2Ps](https://youtu.be/YhmCq-Fb2Ps)

---

## Cálculo de valores pertinentes

### Contas do Circuito

Caso haja algum problema para visualização das equações/relações, aqui está o documento contendo todas as devidas operações [CálculosProjeto1.pdf](./Cálculos%20Projeto%201.pdf)

### 1. Parâmetros Iniciais e Tensão de Pico

O cálculo parte da tensão RMS do secundário do transformador.

* **Tensão Eficaz (Padrão do Projeto):**

    $V_{eficaz} = V_{rms} = 127V$

* **Tensão de Pico da Fonte (antes da retificação):**

    Corresponde à tensão de pico no secundário do transformador.
    $$V_{pico(fonte)} = V_{rms} \cdot \sqrt{2} \approx 179,6V$$

    > É associada à integral da senóide dos dados de funcionamento do transformador.

* **Tensão de Pico do Circuito (pós-retificação):**

   $V_{\text{pico(circuito)}} = V_{\text{pico(fonte)}} \cdot \frac{N_2}{N_1} - 2 \cdot 0.7$ $\cong 179,6 \cdot 0,143 -1,4$

   > $\frac{N1}{N2} =$ Razão inversa de espiras do transformador $=\frac{1}{7}$
   
   > $0.7 =$ Consumo de cada diodo ligado ao transformador

   $\therefore \space V_{\text{pico(circuito)}} \approx 24,28V$
   
   
   > *Observação: Os cálculos subsequentes são baseados neste valor de $V_{pico(circuito)}$.*


### 2. Ripple e Tensão Média

O objetivo é manter uma ondulação (ripple) de tensão em 10%.

* **Tensão de Ripple ($V_{ripple}$):**

    $$V_{ripple} = V_{pico(circuito)} \cdot 0,1 = 24.28V \cdot 0,1 \approx 24,28V$$

* **Tensão Mínima do Circuito ($V_{min}$):**

    $$V_{min(circuito)} = V_{pico(circuito)} - V_{ripple} = 24.28V - 2.428V \approx 21,852V$$

* **Tensão Média do Circuito ($V_{média}$):**

    $$V_{média(circuito)} = \frac{V_{pico(circuito)} + V_{min(circuito)}}{2} = \frac{24.28V + 21.852V}{2} \approx 23,066V$$

### 3. Cálculo do Capacitor de Filtro

A capacitância necessária é calculada com base na corrente da carga, na frequência da rede e na tensão de ripple desejada.

* **Corrente de Carga (Aproximada):**

    $$I_{carga} \approx 101.867mA$$

* **Capacitância ($C$):**

    A fórmula utiliza a frequência do sinal retificado, que é o dobro da frequência da rede para um retificador de onda completa (2 * 60Hz = 120Hz).

    $$C = \frac{I_{aproximada}}{f_{transformador} \cdot V_{ripple}} \approx \frac{0.101867A}{120Hz \cdot 2.428V} \approx 348.77 \mu F$$

    $$C \approx 348.77 \mu F$$, Indica a menor capacitância para o circuito

## Explicação Técnica (Geral)

1. **Fonte de Corrente Alternada (CA) e Transformador**

   A entrada do circuito consiste em uma fonte senoidal padrão da rede elétrica brasileira, com tensão eficaz de 127 V e frequência de 60 Hz.

   Essa fonte está conectada a um transformador rebaixador, que tem a função de reduzir a tensão para valores apropriados ao carregamento (entre, aproximadamente, 3V e 12V, ajustáveis). O transformador também realiza o isolamento galvânico entre a rede elétrica e o circuito de carga, garantindo maior segurança. A relação de espiras (N₁\:N₂) determina o valor da tensão de saída no enrolamento secundário, onde o ‘secundário’ representa a saída, enquanto ‘primário’ representa a entrada. Tem-se a imagem a seguir das especificações dos transformadores presentes para o circuito:

   | Transformador (N°) | Cor Tomada | Voltagem AC | Voltagem no capacitor
   | ---------------------- | ---------------------- | ---------------------- | ----------------------
   | 1      | Preto e Vermelho   | 18.1V | 24.2V  |
   | 2      | Preto e Vermelho   | 18.1V | 24.2V  |
   | 3      | Amarelo - Laranja  | 16.3V | 22V    |
   | 4      | Preto e Vermelho   | 18.1V | 24.2V  |
   | 5      | -                  | 18.1V | 24.2V  |
   | 6      | Preto - Branco     | 11V   | 14.2V  |
   | Alek   | -                  | 12.1V | 14V    |

   Para este projeto, foi utilizado o transformador número 1. No Falstad, foi utilizada a seguinte configuração para o transformador:

   | Configuração                        | Valor                                               |
   | --------------------------------- | ---------------------------------------------------- |
   | Indutância Primária (H)           | 4 |
   | Razão (N1/N2)                     | 7 |
   | Coeficiente de acoplamento        | 0.999 |
   | Aproximação Trapezoidal           | Marcado |
   | Permutar Polaridade Secundária    | Desmarcado |

1. **Ponte Retificadora de Diodos (Retificador de Onda Completa)**

   A ponte retificadora é composta por quatro diodos de silício (ex.: 1N4007) dispostos em configuração clássica de onda completa. Essa topologia converte a corrente alternada do transformador em tensão contínua pulsante, mantendo a polaridade constante nos terminais de saída. Ambas as partes do ciclo da CA são aproveitadas, aumentando a eficiência e a continuidade do fluxo de carga. A tensão de saída ainda possui ondulações (ripple), que são suavizadas por um capacitor.

2. **Capacitor Eletrolítico de Filtro (≥ 348.77 µF)**

   Responsável pela filtragem da tensão pulsante gerada pela ponte de diodos, o capacitor atua como um banco de carga: armazena energia durante os picos de tensão e a libera nos vales, suavizando as oscilações. O valor mínimo, para esse projeto, que pode ser adotado é de 348.77 µF, o suficiente para manter o ripple por volta de 10%.

3. **Resistor de Carga**

   O resistor limita a corrente de saída e dissipa energia em forma de calor, protegendo os componentes sensíveis, como o LED e o transistor, contra sobrecorrentes. Além disso, auxilia no controle da velocidade de descarga do capacitor, estabilizando a resposta do circuito frente a variações rápidas de carga.

4. **Transistor NPN (BJT)**

   O transistor NPN (ex.: BC547 ou 2N2222) funciona como chave de controle ou amplificador de corrente. A condução ocorre quando a base recebe tensão suficiente (tipicamente ≥ 0.7 V), permitindo a passagem de corrente do coletor ao emissor. No circuito, o transistor colabora com o controle de tensão de saída, regulando o fornecimento de energia ao LED e à carga em conjunto com o potenciômetro.

5. **Potenciômetro**

   Um resistor variável, de valor típico 10 kΩ, que permite ajustar a tensão de saída do carregador. Atua diretamente sobre a polarização da base do transistor, controlando sua região de operação. Com isso, é possível definir a tensão final entregue ao dispositivo a ser carregado, variando de forma segura entre, aproximadamente, 3V a 12V.

6. **LED (Diodo Emissor de Luz)**

   O LED serve como indicador visual de funcionamento do circuito. Quando há condução de corrente suficiente, o LED acende, indicando que o circuito está operando corretamente e fornecendo tensão à carga. Sua intensidade luminosa depende da corrente que o atravessa.

7. **Diodo Zener (Regulador de Tensão)**

   O diodo Zener (12 V / 1 W) é responsável por limitar a tensão máxima do circuito. Ele entra em condução quando a tensão atinge seu valor de ruptura em polarização reversa, impedindo que ultrapasse 12 V, protegendo assim os demais componentes e o dispositivo carregado. Atua como regulador passivo de tensão.

8. **Terra (GND)**

   Adicionado na simulação por conveniência visual, não interfere diretamente na funcionalidade elétrica do circuito. Serve como referência de potencial comum e facilita a organização esquemática no ambiente de simulação.

9. **Escolhas de Projeto**
    Durante o desenvolvimento do projeto, houve certas decisões as quais foram tomadas, a fim de se garantir a segurança do funcionamento correto do circuito, sendo elas:
      - O uso de resistores de até 5 W de potência (no caso, os resistores de 100 Ω e de 120 Ω, presentes, respectivamente, antes do transistor NPN e no final do circuito, servindo como a "saída" do carregador);

      - A inserção de um capacitor de 1mF, para garantir a integridade do circuito, em caso de algum pico de corrente do transformador, se a sua especificação variar;

      - A presença de um diodo adicional ao lado do resistor de "saída" do circuito, servindo como proteção adicional meramente. A sua presença é facultativa, podendo ser retirado tranquilamente do circuito, caso se deseje.

## Componentes e Funções (explicação resumida)

| Componente                        | Função                                               |
| --------------------------------- | ---------------------------------------------------- |
| Transformador rebaixador          | Reduz 127 V CA para, aproximadamente, 3–12 V CC e isola galvanicamente |
| Ponte retificadora (1N4007 × 4)   | Converte CA em CC pulsante (onda completa)           |
| Capacitor eletrolítico (≥ 348.77 µF) | Suaviza ondulações, mantendo ripple abaixo de 10%    |
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
