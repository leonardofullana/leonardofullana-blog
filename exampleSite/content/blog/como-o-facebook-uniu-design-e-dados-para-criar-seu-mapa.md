+++
categories = ["Análise de Dados"]
date = 2019-10-29T04:07:47Z
description = "Você sabe o que é um ecossistema de dados e como utilizar esse conceito de forma eficaz mesmo sem ser engenheiro de dados?"
draft = true
image = "/uploads/blogpost-ecossistema-dados.png"
tags = []
title = "Como o Facebook uniu design e dados para criar seu mapa"
type = "featured"

+++
## O Facebook conseguiu muito mais do que um mapa ao unir dados e design.

No final de 2020 o Facebook lançou um mapa global próprio dentro da  plataforma. Isso pode parecer muito ordinário quando pensamos no Google Maps, por exemplo, mas na realidade **o Facebook criou um mapa social.**

### Por que "criar do zero" uma funcionalidade que já existe no mercado?

O objetivo do Facebook com a criação de um mapa próprio foi poder gerar **o senso de localização por meio dos olhos** da própria comunidade, focando muito mais na vizinhança, em parques e locais sociais do que nas tradicionais ruas.

O Facebook Map foi criado pela Stamen, uma empresa especializada em cartografia juntamente com uma equipe de engenheiros, designers e especialistas de dados do Facebook.

Ao unir essas três equipe diferentes o time conseguiu colaborar com dados, ferramental e código ao redor de todo o pipeline de criação dos mapas.

### Como conseguir dados de mapas ao redor do mundo?

Os dados primários por trás do mapa foram obtidos por meio do OpenStreetMap, uma base de dados global e open source, conhecida como a Wikipedia dos Mapas.

O processo de obtenção dos dados foi feito em massa, mas o processo mais complexo começa após a equipe já ter os dados em mãos: **a revisão dos dados.** 

Para garantir a qualidade da revisão, semanalmente era criado um snapshot de todo o processo feito durante aquela semana, para garantir que estava tudo certo.

## Como criar um data lake sem ser engenheiro de dados?

![datalake-sem-engenheiro-de-dados](/uploads/lago-blogpost-datalake.png "Data Lake")

Partindo do pressuposto que você está no pior cenário possível, sem um banco de dados estruturado - com tabelas de dimensões de clientes e fatos transacionais - e sem nenhum sistema que gere inteligência de negócios para a empresa.

Para dar o primeiro passo e começar a criar o seu data lake você só **precisará do bom e velho excel.** Para ser mais específico, você precisará de uma planilha, que eu te recomendo criar no Google Sheets.

A ideia por trás do que criaremos é: ter em uma única aba da sua nova planilha, uma visão geral dos clientes com suas informações demográficas e respectivas compras.

Com isso, acredite se quiser, você poderá começar a criar análises de dados que agregam valor.

## Como estruturar essa planilha do Google Sheets?

![google-sheets-new-spreadsheet-blogpost](/uploads/google-sheets-blogpost.png "Google Sheets")

Antes de mais nada, imagino que você saiba utilizar o Excel. Atualmente ter conhecimento de Pacote Office é básico, e se você está lendo esse artigo acredito que você não esteja no comecinho da sua carreira.

Partindo desse ponto, [abra o Google Sheets, crie uma nova planilha](sheets.new) e crie 3 abas nessa planilha:

1. **Clientes**
2. **Vendas**
3. **Análises**

Estruture as colunas de cada uma das abas dessa sua planilha com as informações relevantes para sua empresa. O exemplo que utilizaremos é de um ecommerce que vende produtos da Apple:

##### Crie a aba de Clientes:

| CPF | Nome | Idade | Estado | Email |
| --- | --- | --- | --- | --- |
| 000.000.000-00 | João da Silva | 48 | Minas Gerais | joao@gmail.com |
| 001.000.000-00 | Cláudia Soares | 26 | São Paulo | claudia@gmail.com |
| 002.000.000-00 | Jorge Pereira | 33 | Rio de Janeiro | jorge@gmail.com |

Preencha essa aba com os dados dos seus clientes, buscando **enriquecer as informações demográficas** o máximo possível que faça sentido para você. Realizar essa tarefa de forma manual ou automatizada é uma resposta que somente você tem, sabendo o tamanho da empresa em que trabalha.

Caso o volume disso seja muito grande, procure viabilizar alguma maneira de automatizar os dados ou busque entender com o setor de TI da sua empresa se já existe um banco de dados estruturado.

##### Crie a aba de Vendas:

| Data | CPF | Valor | Produto | Categoria |
| --- | --- | --- | --- | --- |
| 20/01/2021 | 000.000.000-00 | R$10.600 | iPhone 12 | Celulares |
| 24/01/2021 | 001.000.000-00 | R$1.150 | AirPods 2 | Acessórios |
| 22/01/2021 | 000.000.000-00 | R$35 | Capa protetora para iPhone 12 | Capinhas |
| 31/01/2021 | 000.000.000-00 | R$8.500 | Macbook Air | Notebooks |
| 05/02/2021 | 000.000.000-00 | R$45 | Carregador Lightning | Carregadores |

Nessa aba temos, de forma descendente por data da compra, os pedidos dos clientes, com **o CPF do cliente que comprou, que servirá de chave única** entre as tabelas para cruzar esses dados.

##### Crie a aba de Análises:

Utilizando a função PROCV você conseguirá de forma muito simplificada cruzar os dados de **Clientes + Vendas,** criando um visão completa das vendas.

Mas somente uma visão única por si só não gera valor, este está de fato na **forma como você realizará as análises em cima desses dados.**

## Quais análises de compras mais geram insights?

![analise-compras-insights](/uploads/analises-insights-blogpost.png "Análises de Dados")

Esse é um assunto que eu poderia escrever dezenas de artigos falando sobre, e infelizmente eu não consigo te dar a resposta exata. Isso depende muito do seu cargo, da sua área e, principalmente, da empresa que você trabalha.

Mas em linhas gerais, as principais análises para o exemplo criado seriam:

* **Produtos e categorias** que mais vendem por estado;
* **Faixas etárias** que têm mais adesão por produto;
* Produtos que normalmente são comprados juntos **(basket case analysis);**
* **Análises RFM** (recency - frequency - monetary value);
* Recomendações de **produtos que são comprados em sequência** (ex: quem compra iPhone após duas semanas compra Airpods)
* **Sazonalidade de compra** com base em categoria/produto;
* Sazonalidade de compra por faixa etária;
* **Ticket médio** de compra por faixa etária;
* Valor total gasto em 12 meses **(LTM)** por produto da primeira compra.

A lista de análises é praticamente infinita, mas somente com esses exemplos você já deve ter conseguido imaginar quão valiosas são as informações que você conseguirá extrair dessas análises.

##### Crie personas reais

Você conseguirá criar personas de compra muito mais detalhadas, baseadas em dados reais de cliente, entendendo exatamente como é o comportamento de compra, faixa etária e estado que mora.

##### Calcule o real valor de cada cliente

Com as análises que citei de RFM ou de LTM você consegue mapear de forma muito clara exatamente quanto um cliente vale para você e qual é o seu faturamento projetado com base na frequência de compra dos seus clientes fiéis.

##### Saiba o ROI das suas ações de marketing

Sabendo na ponta do lápis exatamente quanto de faturamento cada cliente gera para sua empresa você consegue calcular exatamente qual é o ROI obtido, em linhas gerais, das campanhas de marketing.

> **ROI é o Retorno Sobre o Investimento**, em %, calculado da seguinte forma: (faturamento - investimento) / investimento.

##### Planeje ações para datas com queda de vendas

Sabendo de antemão exatamente qual é o período que as vendas desaceleram com base na sazonalidade de compra, você consegue planejar ações promocionais com maior assertividade, mantendo o fluxo de caixa da empresa constante.

##### Tenha um ranking de melhores clientes

Você conseguirá obter, de forma muito simples, um ranking com os clientes mais valiosos para sua empresa, podendo criar ações específicas para eles, aumentando ainda mais a sua fidelidade.

##### Mapeie quais são os melhores produtos de entrada

Fazendo uma análise do valor total gasto ao longo de 12 meses (LTM) de seus clientes com base no primeiro produto comprado, você consegue entender qual é a sua melhor "primeira venda", podendo colocar energia de campanhas de marketing focadas nele.

##### Saiba quando ofertar um novo produto

Ao mapear qual a frequência de compra de capinhas de iPhones, por exemplo, você consegue entender exatamente qual é o período de tempo ideal para que você faça uma nova oferta para o cliente do mesmo produto, ou de um muito similar.

## Você precisa de um analista de dados para fazer essas análises?

Em linhas gerais, um profissional especializado nisso conseguirá investir o tempo e energia dele em fazer análises cada vez mais completas e complexas, mas isso não te impede de começar a realizá-las.

**Eu recomendo colocar uma pessoa na empresa/time para pensar somente nisso** sempre que possível, e utilizar o seu tempo para entender como utilizar essas análises para melhorar o negócio e gerar mais valor, de forma inteligente.

## Como colocar a mão na massa e fazer essas análises?

![hands-on-working-data-analysis-blogpost](/uploads/hands-on-working-data-analysis-blogpost.png "Mãos no Notebook Trabalhando")

Eu já te dei o caminho das pedras, agora cabe a você entender como criar esse ecossistema, mapear quais são as análises que poderiam gerar mais valor para o negócio, e especificamente para o seu setor/cargo, e colocar a mão na massa.

Sem dúvida você precisará procurar muita coisa no Google, então não hesite em utilizá-lo. Não é demérito nenhum. Procure o nome das métricas, como são calculadas, exemplos de análises.

E claro, **acompanhe os próximos artigos aqui no blog** para entender ainda mais sobre esse universo de negócios data-driven e product analytics.

Você conseguiu entender o valor por trás de um ecossistema de dados? Pensou em análises que agregarão para o seu negócio?

Se você tiver dúvidas sobre esse assunto, sinta-se a vontade para me chamar no [Instagram @leonardofullana](), me enviar um email ou uma mensagem direta no [LinkedIn](https://linkedin.com/in/leonardofullana).

Ah! Não esqueça de **se increver na caixa abaixo do texto para receber as novas publicações** quentinhas assim que sairem do forno direto no seu email.

Até o próximo artigo!

_Photos by_ [_Unsplash_](https://unsplash.com/s/photos/working-on-laptop?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)_._