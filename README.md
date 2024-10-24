# DataAnalyticsPowerBI


Repósitorio criado para colocar os desafios do curso de Data Analytics

Primeiro desafio:     
A terceira página, a qual vocês irão criar sozinhos, deve conter alguns visuais. Esse desafio visa treinar a habilidade de criação de visuais. Assim, você poderá criar familiaridade com esses recursos. Em módulos mais avançados iremos tratar do layout mais elaborado dos nossos relatórios.  

Muito bem, a terceira página é composta por: 

Visual mapa 1: Soma de sales e unidades vendidas por país 

Visual mapa 2: Soma de lucro (profit) por país 

Visual de pizza: Lucro por segmento 

 

Além disso: 

Verifique a disposição dos visuais no relatório 

Modifique os nomes dos visuais para algo mais claro e direto (de acordo com o contexto) 

Preste atenção aos campos que são utilizados como dicas de ferramentas  

Publique o relatório 

Compartilhe como suplemento no Power Point 

Caso não tenha Power Point, salve o projeto de Power BI  

Desafio Módulo 2:
Instruções de Entrega do Desafio
Descrição do desafio: Você irá criar um relatório mais elaborado com base na sample financials do Power BI. 
Fiquem atentos a: 

Estrutura definida 

Botões de navegação que fornecem navegabilidade 

Segmentadores utilizados e botões com imagem associado 

Utilize os indicadores e botões para selecionar diferentes visuais sobre um mesmo assunto 

 

Utilize os vídeos de passo a passo para criação dos elementos que compõem a primeira página do relatório: 

Objetos que definem o layout do relatório 

Gráficos (visuais) e os campos que os compõem 

Botões para navegabilidade 

Segmentadores de dados 

 

Lembre-se de: 

Criar a segunda página do relatório 

Publique o seu relatório no Power BI Service 

Caso você tenha familiaridade fique livre para utilizar outros artifícios nos botões e outros 

Submenta seu projeto através do link no github 

Terceiro desafio: 
Descrição do desafio módulo 3 – Processamento de Dados Simplificado com Power BI

1. Criação de uma instância na Azure para MySQL

2. Criar o Banco de dados com base disponível no github

3. Integração do Power BI com MySQL no Azure

4. Verificar problemas na base a fim de realizar a transformação dos dados

Diretrizes para transformação dos dados

1. Verifique os cabeçalhos e tipos de dados

2. Modifique os valores monetários para o tipo double preciso

3. Verifique a existência dos nulos e analise a remoção

4. Os employees com nulos em Super_ssn podem ser os gerentes. Verifique se há algum colaborador sem gerente

5. Verifique se há algum departamento sem gerente

6. Se houver departamento sem gerente, suponha que você possui os dados e preencha as lacunas

7. Verifique o número de horas dos projetos

8. Separar colunas complexas

9. Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores. A mescla terá como base a tabela employee. Fique atento, essa informação influencia no tipo de junção

10. Neste processo elimine as colunas desnecessárias.

11. Realize a junção dos colaboradores e respectivos nomes dos gerentes . Isso pode ser feito com consulta SQL ou pela mescla de tabelas com Power BI. Caso utilize SQL, especifique no README a query utilizada no processo.

12. Mescle as colunas de Nome e Sobrenome para ter apenas uma coluna definindo os nomes dos colaboradores

13. Mescle os nomes de departamentos e localização. Isso fará que cada combinação departamento-local seja único. Isso irá auxiliar na criação do modelo estrela em um módulo futuro.

14. Explique por que, neste caso supracitado, podemos apenas utilizar o mesclar e não o atribuir:
    
Mesclar (Merge):
Quando mesclamos os nomes de departamentos e localizações, estamos criando uma nova coluna que contém a combinação desses dois campos. Por exemplo, se tivermos um departamento chamado “Vendas” e uma localização chamada “São Paulo”, a coluna mesclada poderia ser algo como “Vendas - São Paulo”.
Essa abordagem é útil quando queremos criar uma chave composta que seja exclusiva para cada combinação de departamento e localização. Essa chave pode ser usada como a chave primária na tabela de fatos (a tabela central do modelo estrela).

Atribuir (Concatenar):
A concatenação, por outro lado, envolve simplesmente unir os valores dos campos sem criar uma nova coluna. Por exemplo, se tivermos “Vendas” e “São Paulo”, a concatenação seria “VendasSão Paulo”.
No entanto, essa abordagem não é adequada para o nosso caso, porque não garante a exclusividade. Poderíamos ter várias combinações diferentes de departamentos e localizações que resultariam na mesma concatenação. Por exemplo, “Vendas” e “São Paulo” seriam idênticos a “Venda” e “SãoPaulo”.

Além disso, usar a concatenação como chave primária em um modelo estrela pode levar a problemas de integridade e dificultar a agregação de dados.
Portanto, a mesclagem é a escolha mais apropriada aqui. Ela cria uma chave única para cada combinação departamento-local.


16. Agrupe os dados a fim de saber quantos colaboradores existem por gerente

17. Elimine as colunas desnecessárias, que não serão usadas no relatório, de cada tabela

Quarto Desafio:

Descrição do desafio de modelagem dimensional

Objetivo: 
Criar o diagrama dimensional – star schema – com base no diagrama relacional disponibilizado.
Foco:
Professor – objeto de análise
Vocês irão montar o esquema em estrela com o foco na análise dos dados dos professores. Sendo assim, a tabela fato deve refletir diversos dados sobre professor, cursos ministrados, departamento ao qual faz parte.... Por aí vocês já têm uma ideia do que deve compor a tabela fato do modelo em questão. 
Obs.: Não é necessário refletir dados sobre os alunos!
O que deve ser feito?
Deverá ser criada a tabela Fato que contêm o contexto analisado. Da mesma forma, é necessária a criação das tabelas dimensão que serão compostas pelos detalhes relacionados ao contexto.
Por fim, mas não menos importante, adicione uma tabela dimensão de datas. Para compensar a falta de dados de datas do modelo relacional, suponha que você tem acesso aos dados e crie os campos necessários para modelagem. 
Ex: data de oferta das disciplinas, data de oferta dos cursos, entre outros. O formato, ou melhor, a granularidade, não está fixada. Podem ser utilizados diferentes formatos que correspondem a diferentes níveis de granularidade.

Quinto Desafio:

Descrição do Desafio de Projeto

Utilizaremos a tabela única de Financial Sample para criar as tabelas dimensão e fato do nosso modelo baseado em star schema.

O processo consiste na criação das tabelas com base na tabela original. A partir da cópia serão selecionadas as colunas que irão compor a visão da nova tabela. Sendo assim, a partir da tabela principal serão criadas as tabelas:

Financials_origem (modo oculto – backup)


D_Produtos (ID_produto, Produto, Média de Unidades Vendidas, Médias do valor de vendas, Mediana do valor de vendas, Valor máximo de Venda, Valor mínimo de Venda)

D_Produtos_Detalhes(ID_produtos, Discount Band, Sale Price, Units Sold, Manufactoring Price)

D_Descontos (ID_produto, Discount, Discount Band)

D_Detalhes (*)

D_Calendário – Criada por DAX com calendar()

F_Vendas (SK_ID , ID_Produto, Produto, Units Sold, Sales Price, Discount Band, Segment, Country, Salers, Profit, Date (campos))


*Verifique as informações que não foram contempladas nas demais tabelas dimensão que fornecem maiores detalhes sobre vendas.

Quarto desafio:
Desafio de Projeto - Atualizando Relatório Financeiro com Foco na Experiência do Usuário


Objetivo do desafio:

Modificar o relatório criativo, o primeiro que criamos juntos, focando na experiência do usuário. Acompanhe o vídeo para que você entenda o que foi feito neste processo. Além disso, leve em consideração os seguintes pontos:

· Posicionamento

· Contraste

· Proporção áurea

· Segmentação dos dados


Como comentamos no curso, não é uma regra rígida. Entenda os pontos e cria seu relatório levando os em consideração. Contudo, saiba quando você deve quebrar as regras. Isso vai trazer mais criatividade ao seu relatório. Esses pontos fora da curva deixam seu relatório mais interessante.


Próximos passos:

· Insira os botões de navegabilidade

· Modifique a segunda página de forma similar a demostrada no desafio para a primeira página

· Modifique os botões de navegabilidade a fim de destacar o focalizar e selecionar

· Criar os menus de navegabilidade em cada página

· O estilo dos botões é livre!

· O relatório é composto por 3 páginas

Quinto desafio:
Projeto de Data Analytics com Power BI


Pontos a serem considerados

· Crie a página detalhes conforme mostrado no desafio de projeto

· Pense na disposição dos visuais em como o cliente irá consumir o conteúdo

· Dependendo da disposição dos visuais o número de páginas pode variar. Até duas páginas podem compor o que é pedido

· Crie as medidas necessárias


Visuais que podem compor o relatório:

· Visuais sobre os TOP3 Produtos

· Principais países em termos de vendas e/ou profit (ou outro campo)

· Gráfico de dispersão sobre Unidades vendidas e Vendas por mês

· Visuais de agrupamentos de dados

· Visuais de compartimentação dos dados

Último desafio da formação:
 
Instruções para o desenvolvimento
Agora você vai utilizar o relatório do desafio do módulo anterior. Com esse contexto em mãos você irá criar pelo menos dois visuais considerando a criação de parâmetros.

Siga os mesmos passos que fizemos durante o curso para criar os parâmetros de campos. Sendo assim, as diretrizes são:

Primeira visão: parâmetro com base em categorias
Segunda visão: parâmetros com base em valores (profit, sales, ou outros)
Sigam a mesma estilização do relatório
Criem uma história para apresentar essa visão sobre os dados

