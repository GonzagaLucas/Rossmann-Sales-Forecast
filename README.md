**PROJETO EM FASE FINAL**

![image](https://user-images.githubusercontent.com/95088918/159572878-52a943df-c8c8-458f-b2cd-3b3a62ebf331.png)


# 
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Rossmann_Logo.svg/2560px-Rossmann_Logo.svg.png)

*Aviso: O seguinte contexto é completamente fictício, a empresa, o CEO, as questões de negócios foram criadas apenas para desenvolvimento do projeto e se baseiam em um desafio do Kaggle.*

Atualmente, a Rossmann é uma das maiores redes de drogarias da Europa, operando em 7 países, e com mais de 3000 unidades em operação, devido ao grande sucesso de vendas o CEO da companhia deseja reformar todas as suas lojas, dessa forma, foi solicitado aos gerentes que fosse realizado previsões de vendas de suas respectivas lojas para as próximas 6 semanas. As vendas são influenciadas por diversos fatores, como por exemplo: feriados nacionais e escolares, promoções, sazonalidade, localidade, entre outros.

A necessidade de fazer as previsões de vendas das lojas para as próximas 6 semanas será essencial para que o CEO e CFO possa antecipar o valor do budget das respectivas lojas para que todas elas sejam reformadas de acordo com sua realidade, sendo assim, o trabalho desenvolvido nesse projeto será de prever as vendas das próximas 6 semanas para cada uma das lojas de forma assertiva e com resultados confiáveis.

# Planejamento da Solução

1. **Entendimento do negócio e do problema de negócio** -  Entender os motivos por trás da necessidade da previsão de vendas e como resolver o problema, quais aspectos considerar, as features a serem utilizadas e definir qual o melhor algoritmo para a solução.
 
2. **Coleta dos dados** - Coletar os dados disponibilizados pela empresa para utilizá-los na solução do problema.

3. **Limpeza dos dados** - Realizar o tratamento de dados faltantes, outliers, ou dados inconsistentes para que possamos realizar a exploração e preparação desses dados para os próximos passos.

4. **Exploração dos dados** - Nessa etapa faremos uma exploração dos dados para que possamos compreender o negócio, iremos gerar insights através de hipóteses levantadas e buscaremos as variáveis mais importantes para fazermos a modelagem dos algoritmos de Machine Learning.

5. **Preparação dos dados para os algoritmos de machine learning** - Nessa etapa os dados foram transformados e preparados para que os algoritmos ML possam perfomar bem, é fundamental deixar os dados preparados para termos o melhor desempenho possível dos algoritmos, também dividimos os dados entre treino, teste e validação, alem de realizarmos uma cross-validation para termos a certeza que realmente as previsões são confiáveis.

6. **Aplicação e treinamento do algoritmo de machine learning** - Fizemos as seleções dos algoritmos a serem implantadados e o treinamos com os dados já processados e prontos, utilizamos cada algoritmo com seus paramêtros e realizamos também o cross validation para realmente termos certeza da eficácia do algoritmo.

7. **Avaliaçao do modelo** - Aqui fizemos uma avaliação final do modelo para sabermos se já poderia ser feito uma primeira entrega de qualidade do projeto, passando por todos os ciclos do CRISP.

8. **Tradução para negócio** - Finalizado a etapa de preparação, treinamento, aplicação, e previsão usando os modelos de machine learning, nessa etapa traduzimos os resultados obtidos para valores e termos de negócio, para que pessoas sem conhecimento técnico possam entender e compreender os resultados.

9. **Deploy do modelo** - Disponibilizamos o modelo pronto que pode ser acessado através de um bot criado no Telegram, o modelo foi colocado em produção em uma nuvem do Heroku.

# Atributos

| Atributos                        | Explicação                                                      |
| -------------------------------- | ------------------------------------------------------------ |
| Id                               | Um Id que representa uma dupla (Store, Date) dentro do conjunto de teste |
| Store                            | Um id único para cada loja                                   |
| Sales                            | O volume de vendas para qualquer dia                         |
| Customers                        | O número de clientes em um determinado dia                       |
| Open                             | Um indicador para saber se a loja estava aberta: 0 = fechada, 1 = aberta |
| StateHoliday                     | Indica um feriado estadual. Normalmente todas as lojas, com poucas exceções, fecham nos feriados estaduais. Observe que todas as escolas fecham nos feriados e finais de semana. a = feriado, b = feriado da Páscoa, c = Natal, 0 = Nenhum |
| SchoolHoliday                    | Indica se (Loja, Data) foi afetado pelo fechamento de escolas públicas |
| StoreType                        | Diferencia entre 4 modelos de loja diferentes: a, b, c, d  |
| Assortment                       | Descreve um nível de estoque: a = básico, b = extra, c = estendido |
| CompetitionDistance              | Distancia em metros do competidor mais proximo           |
| CompetitionOpenSince[Month/Year] | Dá o ano e mês aproximados em que o concorrente mais próximo foi aberto |
| Promo                            | Indica se uma loja está fazendo uma promoção naquele dia         |
| Promo2                           | Promo2 é uma promoção contínua e consecutiva para algumas lojas: 0 = a loja não está participando, 1 = a loja está participando |
| Promo2Since[Year/Week]           | Descreve o ano e a semana em que a loja começou a participar da Promo2 |
| PromoInterval                    | Descreve os intervalos consecutivos de início da promoção 2, nomeando os meses em que a promoção é iniciada novamente. Por exemplo. "Fev, maio, agosto, novembro" significa que cada rodada começa em fevereiro, maio, agosto, novembro de qualquer ano para aquela loja |

# Top 3 Insights

**1. Lojas vendem mais depois do dia 10 de cada mẽs**

![image](https://user-images.githubusercontent.com/95088918/159571814-62036a6f-02eb-4c39-8f2d-5176d8dfe1e5.png)

**2. Lojas com maior sortimento vendem menos**

![image](https://user-images.githubusercontent.com/95088918/159572208-5065c562-f7c9-4e28-9d3a-0ca7f2aaf992.png)

**3. Lojas vendem menos aos finais de semana**

![image](https://user-images.githubusercontent.com/95088918/159572568-b2257f1b-af5f-4ec6-81aa-a0519ad5f052.png)

# Modelos de Machine Learning Utilizados Durante o Projeto

Utilizamos os seguintes algoritmos para fazermos as previsões:
- Modelo de média para termos uma base de comparação para os modelos posteriores
- Linear Regression;
- Linear Regression Regularized (Lasso);
- Random Forest Regressor;
- XGBoost Regressor. 

**RESULTADOS OBTIDOS COM APLICAÇÃO DO CROSS VALIDATION**

| Model Name | MAE CV   | MAPE CV      | RMSE CV |
|-----------|---------|-----------|---------|
|  Random Forest Regressor  | 837.17 +/- 219.74| 0.12 +/- 0.02  | 1256.87 +/- 319.67 |
|  XGBoost Regressor	  | 1030.28 +/- 167.19 | 0.14 +/- 0.02   | 1478.26 +/- 229.79 |
|  Linear Regression	  | 2081.73 +/- 295.63 | 0.3 +/- 0.02   | 2952.52 +/- 468.37 |
|  Lasso	  | 2116.88 +/- 341.01 | 0.3 +/- 0.01	   | 3057.6 +/- 504.57 |
