Avaliação Técnica – Séries Temporais

O objetivo desse projeto é avaliar seus conhecimentos na análise e modelagem de séries temporais, como tratamento de dados, descoberta de padrões, e a criação e validação de modelos.

Objetivo
O objetivo é prever o comportamento da quantidade total de passageiros saindo do país (`Passengers In`).


Após tratamento de dados análise de decomposição de série temporal do arquivo international_airline_activity_table1_2009tocurrent_0122.xlsx, foi possível obter as seguintes conclusões e observações:

![image](https://user-images.githubusercontent.com/94915093/163629570-e181f9a9-e5cc-4b28-adf3-1166eb40ae0d.png)

- Nota-se claramente a presença de sazonalidade em período aproximadamente de 30 dias, com base no gráfico acima.
- Tendência positiva e quebra de regime por volta do 120º dia, com inversão da autocorrelação a partir desse ponto.

![image](https://user-images.githubusercontent.com/94915093/163629817-0a7f48c0-094f-441b-81fb-22cb70f65f0d.png)

Após teste de estacionariedade, verificou-se a não-estacionariedade da série temporal:
![2022-04-15_17h38_22](https://user-images.githubusercontent.com/94915093/163629884-ffbb60ed-2151-4f65-8521-1eb0f1905ee6.png)

Foram executados 4 simulações de auto-arima com o coeficiente m=1 (anual), m=7 (diário), m=12 (mensal) e m=52 (semanal).
Das quais obteve-se os parâmetros p,d,q abaixo:

m=1:
- SARIMAX(3, 1, 2)

m=7:
- SARIMAX(4, 1, 4)x(1, 0, [1], 7)

m=12:
- SARIMAX(4, 1, 2)x(2, 0, [], 12)	

m=52
- SARIMAX(3, 1, 2)


Definiu-se a base de treino de até 6 meses antes do último registro e a base de treino, os últimos 6 meses de registro.

Com as simulações descritas anteriormente, foi possível observar as seguintes predições:
![image](https://user-images.githubusercontent.com/94915093/163630210-b56a40e0-bbfe-4558-91f5-fbb578aedbc0.png)
![2022-04-15_17h43_20](https://user-images.githubusercontent.com/94915093/163630241-f171ef1f-cfc1-463b-a62e-777c1933b21a.png)

Fica evidente que a simulação m12 obteve uma melhor performance, analisando o RMSE e o coeficiente de variação.

Concluindo-se essa etapa, obteve-se a previsão para os próximos 6 meses, com as 4 simulações:
![image](https://user-images.githubusercontent.com/94915093/163630353-c3363de9-d720-4e21-8085-3272b2b11413.png)


Ao utilizar-se a base de dados presente no repositório: https://raw.githubusercontent.com/lukes/ISO-3166-Countries-with-Regional-Codes/master/all/all.csv, foi possível dividir o dataframe original em 5 continentes: África, Américas, Ásia, Europa e Oceania.

Repetindo-se os passos anteriores para cada base de dados de continentes, foi possível obter o RMSE e a previsão de 6 meses para cada continente:

![2022-04-15_17h47_34](https://user-images.githubusercontent.com/94915093/163630540-5db8cab1-e253-4261-952b-2937a02698e0.png)
![2022-04-15_17h47_58](https://user-images.githubusercontent.com/94915093/163630567-b1b41da7-e189-46cd-8d36-c508d9738309.png)
![2022-04-15_17h48_17](https://user-images.githubusercontent.com/94915093/163630591-809788f9-bcc7-4424-b93d-7554c2bddcb7.png)
![2022-04-15_17h48_41](https://user-images.githubusercontent.com/94915093/163630615-72d961dc-6054-4e8f-a1d7-554a68076acb.png)
![2022-04-15_17h48_57](https://user-images.githubusercontent.com/94915093/163630626-e07be164-8df3-41cd-90ce-4784d50cb91d.png)

É possível perceber que a variação por país é muito maior do que a primeira análise, que somente utiliza-se da data para a predição.

Os modelos foram salvos em formato .pkl e estão disponíveis nesse diretório para download e reuso.





