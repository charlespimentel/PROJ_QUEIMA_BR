
﻿|![](Aspose.Words.cadbdee8-61c8-4d0f-90ff-84bfc9ba6aaf.001.png)|**TERMO DE ABERTURA DO PROJETO** |
| :- | :-: |
||**NOME DO PROJETO: Determinação da natureza das queimadas, se provocada pelo homem, se ocorreu naturalmente e predição de queimadas futuras no Brasil**|
||**CÓDIGO DO PROJETO: 001**|


|**Histórico de Revisão**|
| :- |

Versão | Data | Descrição da Revisão | Autores
------------ | ------------- | ------------- | -------------
V2 | 18/03/2021 | Segunda versão do projeto | Mauro Bastos Ronilson Pinho e Charles Pimentel

|**1 – Nome do Projeto**|**2.1 – Código do Projeto**|
| :- | :- |
|**Determinação da natureza das queimadas, se provocada pelo homem, se ocorreu naturalmente e predição de queimadas futuras no Brasil**|*PROJ\_QUEIMA\_BR*|

|**2 – Nome dos Gerentes do Projeto**|
| :- |
|*Mauro Penha Bastos, Ronilson Pinho e Charles Pimentel*|

|**3 – Alinhamento estratégico - Abstract**|
| :- |
|<p>*Resolver a dificuldade de entender o quanto as queimadas no Brasil são causadas pelo homem e quanto são naturais.*</p><p>*Determinar a probabilidade de queimadas para os próximos cinco anos nos diversos biomas estudados.*</p><p>*Nesse contexto o método criará parâmetros acompanhados de probabilidades, que permitirá que todas as partes interessadas nacionais e internacionais possam aferir se as queimadas que ocorrem no Brasil foram causadas pelo homem e quais foram causadas pela natureza, acompanhada de uma probabilidade, que informa o grau de certeza.. O método irá evitar a escalada de incêndios, através da responsabilização dos órgãos governamentais da área, caso o sistema aponte para ações antinaturais, além de melhorar a saúde da população, ao evitar incêndios.*</p><p>*Sabemos que as queimadas causam inúmeros danos ao solo, principalmente na questão nutricional. Ele altera, direta ou indiretamente, as características físicas, químicas, morfológicas e biológicas. Sabendo disso e obtendo três dataset sobre queimadas da base do INPE entre  2015 e 2019. Pretendemos desenvolver um trabalho baseado em IA (inteligência Artificial) que possa predizer se as ações de queimadas nessa região é provocada por ação natural ou não.*</p> <p>*A missão do método é estabelecer uma base para que as queimadas possam ser aferidas e previstas por qualquer que seja o governo ou, grupo interessado possa verificar os eventos e trazer credibilidade para os governos no Brasil.*</p> <p>*Hoje temos uma lacuna na fiscalização da procedência das queimadas, e pretendemos solucionar o problema com a medição de queimadas e predizendo as futuras queimadas naturais. Desse modo nosso método cria uma base que prioriza o meio ambiente e permite que qualquer pessoa afira de forma clara se uma queimada foi natural ou não e que os governos possam se preparar para as futuras queimadas previstas.*</p>
  
|**4 – Objetivos do projeto** |
| :- |
|<p>*Resolver a dificuldade de entender o quanto as queimadas no Brasil são causadas pelo homem e quanto são naturais, e determinar a probabilidade de queimadas para os próximos cinco anos nos diversos biomas estudados.*</p><p>- *Predizer em forma de probabilidade, quando vai haver queimada baseado nos eventos passados;*</p><p>- *Determinar através de um método supervisionado os fatores que mais contribuem para as queimadas, acompanhados de suas respectivas probabilidades, usando árvore de classificação;*</p><p>- *Determinar através de um método supervisionado se as queimadas, são naturais ou não acompanhados de suas respectivas probabilidades, usando árvore de classificação;*</p><p>- *Determinar através de um método não supervisionado se o padrão de queimada é natural ou não (Redes Neurais);*</p><p>- *Prover para o Brasil um método de predição de queimadas pera os próximos cincos anos usando árvore de regressão.*</p><p>- *Reduzir queimadas, trazer credibilidade para o Brasil sobre a gestão do meio ambiente.*</p>|

|**5 – Modelo de Dados do Experimento**|
|![](Modelo.de.Dados.do.Experimento.png)| 

|**6 – Descrição do DataSet e suas fontes**|
| :- |
|<p>*Recuperamos a base de queimadas e chuvas de 5 anos no Brasil e os Datasets tem as seguintes características.*</p><p>**1)	Dados brutos (RAW): Dataset dos incêndios nos Biomas do Brasil:**</p><p>a) *TXT baixado no dia 7/03/2021 às 14:03, do site www.inpe.gov.br contendo informações de todos os incêndios do Brasil dos anos de 2012 e 2019, chamado “incendios_em_unidades_de_conservacao_federal.csv”.*</p><p>b) *Dados transferidos sem modificação via Python3 rodando em Windows 10 Professional para a tabela “queima_Excel” em banco PostgreSql versão 9.5.*</p><p>**2) Dados brutos (RAW): Dataset de chuvas com atributos a serem transformados para que os dados de queimadas, seja enriquecido:**</p><p>a) *TXT baixado no dia 15/03/2021 às 18:42, do site www.inmet.gov.br contendo informações de chuvas em todos os biomas do Brasil dos anos de 2010 e 2011, chamado “Vs_2_1_Focos_2010-01-01_2011-01-01.csv”, contendo 1.048.576 registros.*</p><p>b) *Carregado em um Dataframe via Python3 rodando em Windows 10 Professional, e retirada as colunas x, y e agrupado por estado, município, e bioma gerando a tabela “chuvas” no banco de dados PostgreSql versão 9.5 reduzidos a 5,578 registros.*</p><p>c) *Na carga da base chuvas, foram achadas a latitude e longitude.*</p><p>**Decomposição das bases de queimadas e chuvas em tabelas:**</p><p>1- *Dados de Informação do Bioma.*</p><p>2- *Dados de eventos de queimadas.*</p><p>3- *Chuvas.*</p><p>**Limpeza dos dados:**</p><p>1- *Foi detectada entre os 1.045.575 linhas de chuva, uma linha com o campo bioma em branco e pode ser atualizado para “Pampas”, através do estado e município.*</p><p>2- *Os dados anuais de eventos não ocorridos, foram zerados de modo a contar como quantidade, mas não contar como valor no algoritmo de predição.*</p><p>*3-	Como o objetivo na tabela de chuvas é localizar (latitude e longitude) o bioma, e existiam milhares de valores diferentes para um único bioma, os mesmos foram substituídos pelas médias das latitudes e as médias das longitudes.*</p>|

|**7 – Experimento**|
| :- |
|<p>**1) Estágio atual do projeto:**</p><p>*a. Definimos o experimento.*</p><p>*b. Obtivemos os datasets de entrada .*</p><p>*c. Definimos todas as tabelas.*</p><p>*d. Carregamos RAW.*</p><p>*e. Fizemos as extrações, as transformações, e as carga  das informações necessárias.*</p><p>**2) Foram criadas 4 tabelas de trabalho, conforme modelo de dados.**</p><p>**3) As informações de proveniência foram colocadas em script Python3 no Github, conforme descrito no item 6.**</p><p>**4) Iremos gerar a tabela “experimento” a partir das demais tabelas para início dos experimentos de classificação de eventos “Naturais” ou “Provocados Pelo Homem” dependendo do resultado de cada uma das queimadas.**</p><p>**5) Na próxima semana iremos programar o experimento e preparar o experimento de predição de novas queimadas com o mesmo Dataset “experimento”.**</p>|

|**8 – EAP do Projeto**|
| :- |
|<p>*WBS do Projeto ( EAP – Estrutura Analítica do Projeto)*</p><p>*A EAP vai ser finalizada na semana de 25/03/2021*</p>|

|**9 – Estimativa de Usuários**|
| :- |
|<p>*58 milhões de pessoas afetadas pelas queimadas diretamente nos diversos estados do Brasil*</p><p>*Fonte: IBGE mar/2021  - xxxxxxxx*</p>|

|**10 – Prazo do Projeto**|
| :- |
|*240  horas de trabalho – 60 horas / semana = 4 semanas*|

|**11 – Equipe de Gestão do Projeto**|
| :- |

Função no Projeto | Nome | Lotação | Telefone | E-mail
------------ | ------------- | ------------- | ------------- | -------------
Orientadores | Sérgio Serra e Jorge Zavaleta | UFRJ - NCE | 21 | E-mail
Doutorandos | Mauro, Ronilson e Charles | UFRJ - NCE | 21 | auropbastos@gmail.com, ronilsonpinho@gmail.com, pimentelufrj@gmail.com

|**12 – Scripts do Projeto**|
| :- |
|*Arquivos_V.2*|

|**13 – Scripts Python**|
| :- |
|*Arquivos_V.2*|

|**14 – Modelo de Script postgreSql para captura de TXT**|
| :- |
|*Arquivos_V.2*|

|**15 – Restrições**|
| :- |
|<p>*1.A conclusão do projeto ocorrerá na segunda semana de 04/2021.*</p><p>*2.As detecções de queimadas futuras terão um resultado probabilístico e devemos entender nos próximos dias se os dados atuais conseguem gerar essa previsão.*</p><p>*3.Deverá haver um protótipo funcional e rodando antes da apresentação final do projeto.*</p>|

|**16 – Documentos de Referência**|
| :- |
|<p>Lei nº xxxxxxx dos Institutos Federais de 29 de dezembro de 2008.http://www.imp.gov.br</p><p>Instrução Normativa nº 04 de 12 de novembro de 2010.</p><p>http://www.governoeletronico.gov.br/sisp-conteudo/nucleo-de-contratacoes-de-ti/modelo-de-contratacoes-normativos-e-documentos-de-referencia/instrucao-normativa-mp-slti-no04/*</p>|

*
*
*
*
*
|![](Aspose.Words.cadbdee8-61c8-4d0f-90ff-84bfc9ba6aaf.001.png)|**TERMO DE ABERTURA DO PROJETO** |
| :- | :-: |
||**NOME DO PROJETO: Determinação da natureza das queimadas, se provocada pelo homem, se ocorreu naturalmente e predição de queimadas futuras no Brasil**|
||**CÓDIGO DO PROJETO: 001**|


|**Histórico de Revisão**|
| :- |

Versão | Data | Descrição da Revisão | Autores
------------ | ------------- | ------------- | -------------
V1 | 11/03/2021 | Primeira versão do projeto | Mauro Bastos Ronilson Pinho e Charles Pimentel

|**1 – Nome do Projeto**|**2 – Código do Projeto**|
| :- | :- |
|**Determinação da natureza das queimadas, se provocada pelo homem, se ocorreu naturalmente e predição de queimadas futuras no Brasil**|*PROJ\_QUEIMA\_BR*|

|**3 – Nome dos Gerentes do Projeto**|
| :- |
|*Mauro Penha Bastos, Ronilson Pinho e Charles Pimentel*|

|**4 – Alinhamento estratégico - Abstract**|
| :- |
|<p>*Resolver a dificuldade de entender o quanto as queimadas no Brasil são causadas pelo homem e quanto são naturais.* </p><p>*Determinar a probabilidade de queimadas para os próximos cinco anos nos diversos biomas estudados.* </p><p>*Nesse contexto o método criará parâmetros acompanhados de probabilidades, que permitirá que todas as partes interessadas, nacionais e internacionais, possam aferir se as queimadas que ocorrem no Brasil foram causadas pelo homem e quais foram causadas pela natureza, acompanhada de uma probabilidade, que informa o grau de certeza. O método irá evitar a escalada de incêndios, através da responsabilização dos órgãos governamentais da área, caso o sistema aponte para ações antinaturais, além de melhorar a saúde da população, ao evitar incêndios.*</p><p>*Sabemos que as queimadas causam inúmeros danos ao solo, principalmente na questão nutricional. Ele altera, direta ou indiretamente, as características físicas, químicas, morfológicas e biológicas. Sabendo disso e obtendo três dataset sobre queimadas da base do INPE entre  2015 e 2019, pretendemos desenvolver um trabalho baseado em IA (inteligência Artificial) que possa predizer se as ações de queimadas nessa região é provocada por ação natural ou não*. </p><p>*A missão do método é estabelecer uma base para que as queimadas possam ser aferidas e previstas por qualquer que seja o governo, ou grupo interessado, que deseje verificar os eventos e trazer credibilidade para os governos no Brasil.* </p><p>*Hoje temos uma lacuna na fiscalização da procedência das queimadas, e pretendemos solucionar o problema com a medição de queimadas e predizendo as futuras queimadas naturais. Desse modo nosso método cria uma base que prioriza o meio ambiente e permite que qualquer pessoa afira de forma clara se uma queimada foi natural ou não e que os governos possam se preparar para as futuras queimadas previstas.*</p>|

|**5 – Objetivos do projeto** |
| :- |
|<p>*Resolver a dificuldade de entender o quanto as queimadas no Brasil são causadas pelo homem e quanto são naturais, e determinar a probabilidade de queimadas para os próximos cinco anos nos diversos biomas estudados.* </p><p>- *Predizer em forma de probabilidade, quando vai haver queimada baseado nos eventos passados;*</p><p>- *Determinar através de um método supervisionado os fatores que mais contribuem para as queimadas, acompanhados de suas respectivas probabilidades, usando árvore de regressão.*</p><p>- *Determinar através de um método supervisionado se as queimadas, são naturais ou não acompanhados de suas respectivas probabilidades, usando árvore de classificação.*</p><p>- *Determinar através de um método não supervisionado se o padrão de queimada é natural ou não (Redes Neurais).*</p><p>- *Prover para o Brasil um método de predição de queimadas pera os próximos cincos anos usando árvore de regressão.*</p><p>- *Reduzir queimadas, trazer credibilidade para o Brasil sobre a gestão do meio ambiente.*</p>|

|**6 – Descrição do DataSet e suas fontes**|
| :- |
|<p>*Recuperamos a base de queimadas de 5 anos no Brasil e o dataset tem as seguintes características:* </p><p>1) *Não foi possível nos concentramos no dataset do Pantanal*</p><p>2) *Estamos tendo dificuldades de encontrar um dataset de chuvas que possua um atributo que se ligue com as bases de queimadas* </p><p>*Pretendemos decompor a base de queimadas em duas bases:* </p><p>1) *Dados de Informação do Bioma*</p><p>2) *Dados de eventos de queimadas*</p><p>*Limpeza dos dados:*</p><p>1) *Os dados de eventos não ocorridos serão zerados de modo a contar como quantidade, mas não contar como valor*</p>|

|**7 – EAP do Projeto**|
| :- |
|<p>*WBS do Projeto ( EAP – Estrutura Analítica do Projeto)*</p><p>*A evoluir ........*</p><p></p><p></p>|

|**8 – Estimativa de Usuários**|
| :- |
|<p>*58 milhões de pessoas afetadas pelas queimadas diretamente nos diversos estados do Brasil*</p><p>*Fonte: IBGE mar/2021  - xxxxxxxx*</p>|

|**9 – Prazo do Projeto**|
| :- |
|*240  horas de trabalho – 60 horas / semana = 4 semanas*|

|**10 – Equipe de Gestão do Projeto**|
| :- |

Função no Projeto | Nome | Lotação | Telefone | E-mail
------------ | ------------- | ------------- | ------------- | -------------
Orientadores | Sérgio Serra e Jorge Zavaleta | UFRJ - NCE | 21 | E-mail
Doutorandos | Mauro, Ronilson e Charles | UFRJ - NCE | 21 | auropbastos@gmail.com, ronilsonpinho@gmail.com, pimentelufrj@gmail.com

|**11 – Restrições**|
| :- |
|<p>1. *A conclusão do projeto ocorrerá na segunda semana de 04/2021*</p><p>2. *Não será possível fazer a parte de detecção de queimada natural ou não, se não conseguirmos um dataset de chuvas com uma chave de conexão com o dataset de queimadas*</p><p>3. *Deverá haver um protótipo funcional e rodando antes da apresentação final do projeto*</p>|


|<h5>**12 – Documentos de Referência**</h5>|
| :- |
|<p>Lei nº xxxxxxx dos Institutos Federais de 29 de dezembro de 2008.<br>http://www.imp.gov.br</p><p>Instrução Normativa nº 04 de 12 de novembro de 2010.<br>http://www.governoeletronico.gov.br/sisp-conteudo/nucleo-de-contratacoes-de-ti/modelo-de-contratacoes-normativos-e-documentos-de-referencia/instrucao-normativa-mp-slti-no04/</p>|
