# LSTM

## 1) Teoria:

![LSTM - célula completa](https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/Figuras_teoria/4_lstm_bloco_complexo.png)

A variável chamada de Ct-1 e Ct. Da mesma forma que temos um estado anterior e o próximo estado que chamamos de h, aqui também há uma espécie de estado anterior e um próximo estado
 
![LSTM - variável Ct](https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/Figuras_teoria/1_lstm_variavel_ct.png)

Então, na prática, se o valor que está saindo da sigmoide for igual a 1, o valor após a multiplicação fica inalterado, e assim nada mudou na saída: o filtro deixou passar tudo. Se a saída da sigmoide for 0, não importa a entrada, ela será zerada; ou seja, o filtro está barrando tudo.
 
![LSTM - cálculo do sigmoide](https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/Figuras_teoria/1_lstm_calculos_sigmoide.png)

Ela é gerada a partir da entrada de xt: a entrada é que gera o estado Ct, com base na entrada do estado anterior que ainda não vimos. A entrada xt é o dado principal que está fomentando a criação do Ct a partir de uma função de ativação.

Essa entrada Ct passa por alguns pesos e bias. Ela possui pesos diferentes do que vimos anteriormente na sigmoide, apesar de estarmos usando as mesmas entradas (o filtro da sigmoide usava o ht-1 e o xt também). Como há outra função de ativação, um outro bloco, há pesos diferentes, com outra calibração.

![LSTM - cálculo da variável Ct 2](https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/Figuras_teoria/2_lstm_calculos_variavel_ct_2.png)

Memória de longo prazo
A nossa Ct, se formos analisar ao longo do tempo, e se todos os filtros forem 1, será nada mais que uma soma do Ct-1, com o Ct-2, com o Ct-3, etc. Isso é muito relevante, porque se lembrarmos de uma rede neural recorrente, veremos que a cada novo estado, o estado anterior era diluído pela metade (que acontecia porque aquela retroalimentação estava entrando com uma nova entrada xt e o estado ht-1).

Então, sempre diluímos o estado anterior pela metade a cada nova iteração, e isto fazia com que os valores das entradas antigas fossem reduzidos muito rapidamente; depois de oito ou dez iterações, praticamente nem se considerava mais os valores das entradas antigas. Eles eram totalmente esquecidos pela rede.

Memória de curto prazo
Esse outro filtro aqui ao lado definirá o quanto vale a pena reduzir no dado atual, porque a rede pode perceber que o dado gerado agora, por algum motivo, passou um valor que vale a pena não reduzir e deixar passar integralmente.

Esse filtro controla o curto prazo: se vale a pena reduzir cada momento instantâneo ou não. Então temos esse ajuste fino de dois filtros controlando o curto e o longo prazo, e aí fazemos aquela alusão ao Long Short-Term Memory – memória de longo e curto prazo.

![LSTM - cálculo de ht - 1](https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/Figuras_teoria/3_lstm_calculos_ht-1.png)

Cálculo do ht
Entendido isso, agora vamos ver a última parte do bloco, que gera o ht. O ht nada mais é que o próprio Ct que acabamos de ver, só que ele passa por uma função de ativação.

Vamos considerar que o Ct é uma memória de longo prazo (a soma das memórias anteriores, passando por alguma atenuação dos filtros) e, agora, vamos passar o resultado dessa memória de longo prazo para uma função de ativação e haverá mais um filtro aplicado sobre ele. É isso que gerará o estado ht.

O ht nada mais é que a memória de longo prazo atenuada pelo resultado do curto prazo. Essa é a diferença do ht para o Ct: o ht é o Ct passando por uma função de ativação e por um filtro, calibrados a partir da entrada atual e do ht-1.


## 2) Banco de dados de séries temporais:
(Aplicando asos dados de passageiros e bla bla bla... temos o seguinte resultado:)

## 3) Resultado do modelo:

![Previsão final do LSTM](https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/1961_4_months_prevision_passangers.png) 

Zoom na previsão final:
![Zoom da Previsão final do LSTM](https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/Zoom_1961_4_months_prevision_passangers.png)

Referências:
https://github.com/Ibsen-Gomes/LSTM_Neural_Network/blob/main/Teoria_LSTM
