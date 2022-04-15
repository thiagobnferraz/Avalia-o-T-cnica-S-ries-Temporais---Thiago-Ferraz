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





