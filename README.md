# Projeto de Ciência de Dados: Identificando Jogadores Semelhantes a Mbappé através de Clusters

**9 de junho de 2024**
Neste início de maio, comecei o MBA de Ciência de Dados e Analytics da MBA USP/Esalq onde tive aulas de introdução à estatística e de programação em Python, que foram extremamente interessantes. No final de maio e começo de junho, avançamos para as disciplinas de Aprendizado de Máquinas Não Supervisionadas, onde tive ótimas aulas sobre clusters. Inspirado pelas aulas do professor Wilson Tarantin Junior, decidi aplicar o que aprendi em um projeto prático.

Para quem me acompanha no LinkedIn, sabem que já publiquei artigos sobre análise de desempenho e mercado de futebol, uma das minhas paixões. Utilizei esse conhecimento para desenvolver este primeiro trabalho de clusterização.

## Objetivo do Projeto

Como todos sabem, Kylian Mbappé acaba de assinar com o Real Madrid, o que é o assunto do momento. Mbappé, um dos melhores atacantes do mundo, agora faz parte do multi-campeão Real Madrid, ao lado de estrelas como Bellingham, Vinicius Junior e Rodrygo. Dada sua enorme importância no mercado do futebol, meu objetivo era identificar jogadores com um perfil estatístico semelhante ao de Mbappé.

## Coleta de Dados

Utilizando a base de dados do FBref, fiz um webscraping das principais ligas europeias (Bundesliga, Eredivisie, La Liga, Ligue 1, Serie A, Premier League e Primeira Liga), focando apenas nas ligas nacionais e excluindo competições como a Champions League. Coletei dados de 3298 jogadores e, após filtrar para incluir apenas atacantes, restaram 1248 jogadores.

## Seleção das Categorias

As categorias selecionadas para a análise foram:

**Jogador  
Nação  
Equipe  
Jogos Disputados  
Jogos Iniciados (jogos como titular)  
Gols  
Assistências  
Pênaltis Batidos  
Pênaltis Convertidos  
Cartões Amarelos Recebidos  
Cartões Vermelhos Recebidos**  
**XG** (Expectativa de Gols)  
**XAG** (Expectativa de Assistências)  
**Carregadas Progressivas -** (movimentos com a bola que avançam pelo menos 10 jardas em direção ao gol adversário ou entram na área de pênalti, exceto se terminarem na metade defensiva do campo)  
**Passes Progressivos -** (passes completados que avançam pelo menos 10 jardas em direção ao gol adversário ou entram na área de pênalti, exceto se forem feitos na parte defensiva do campo)  
**Passes Progressivos Recebidos**

## Análise Inicial dos Dados

Inicialmente, utilizei um boxplot para entender como os dados estavam distribuídos. O retângulo azul do boxplot indica onde a maioria dos dados está centralizada, enquanto os pontos isolados indicam dados acima do normal, geralmente representando os melhores jogadores.
![enter image description here](https://media.licdn.com/dms/image/v2/D4D12AQEExtf9M4au7w/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1721203828730?e=1734566400&v=beta&t=CqtqaopBW6s0Q8vFK1glK0IGB6k-SRmtuF73_mgAorY)
Vendo os dados distribuídos no boxplot, consegui perceber que a maioria dos atacantes segue um padrão, enquanto os de elite se destacam significativamente. Isso me faz acreditar que posso separar bem os jogadores de elite dos demais.

## Métodos de Agrupamento

Seguindo o que foi ensinado nas aulas da USP Esalq, foquei em identificar o melhor método para agrupar os dados. Testei inicialmente com dendrogramas para o método Hierárquico Aglomerativo, mas não obtive resultados satisfatórios. Parti então para o método K-means, utilizando os métodos Elbow e Silhouette para determinar a quantidade ideal de clusters. Decidi separar os dados em 4 clusters:

**Cluster 1:** 61 jogadores  
**Cluster 2:** 174 jogadores  
**Cluster 3:** 389 jogadores  
**Cluster 4:** 624 jogadores

## Análise dos Clusters

Foquei na análise dos atacantes dos Clusters 1 e 2, reduzindo a lista de 1248 para 238 jogadores. Os atacantes do Cluster 1 são mais matadores, com melhores estatísticas em bater e converter pênaltis. Em contraste, os jogadores do Cluster 2, apesar de também terem números elevados de gols, se destacam por carregar mais a bola. Exemplos disso são Harry Kane e Kylian Mbappé no Cluster 1, enquanto Vinicius Júnior e Phil Foden estão no Cluster 2.

Podemos ver o resultado desta análise nos scatterplots a seguir.
![enter image description here](https://media.licdn.com/dms/image/v2/D4D12AQHvAFprFhodcA/article-inline_image-shrink_1000_1488/article-inline_image-shrink_1000_1488/0/1721178626822?e=1734566400&v=beta&t=vEWT7kJqZtdMNOXrUCuTT9rU8tBo6GKBn1L3ruHvSFg)
![enter image description here](https://media.licdn.com/dms/image/v2/D4D12AQHyEFLrJSKOSA/article-inline_image-shrink_1000_1488/article-inline_image-shrink_1000_1488/0/1721203102987?e=1734566400&v=beta&t=0kfhvU1sEdE3oPTpHQg0NopTq4G9ggqgaborS9f-02U)
## Refinando a Análise

Insatisfeito com a grande quantidade de jogadores no Cluster 1, refiz o processo de clusterização, focando apenas nos 61 jogadores deste grupo. Novamente utilizei os métodos Elbow e Silhouette e optei por trabalhar com 4 clusters. Fiz outro boxplot para ver a distribuição dos dados, e desta vez identifiquei que havia mais valores dentro da média e apenas alguns isolados, indicando jogadores com perfis mais parecidos, graças à nossa filtragem.
![enter image description here](https://media.licdn.com/dms/image/v2/D4D12AQGy_UQXDb56zg/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1721187801883?e=1734566400&v=beta&t=YfTv5wqXAyWAZGBCthRhkRBgFBMiH0M7efOIO7-3uyg)

O scatterplot abaixo mostra como os jogadores estão posicionados, incluindo Mbappé.
![enter image description here](https://media.licdn.com/dms/image/v2/D4D12AQGOlrMeKF0HFQ/article-inline_image-shrink_1000_1488/article-inline_image-shrink_1000_1488/0/1721204804607?e=1734566400&v=beta&t=FroEyIp0bcuZ4qaKfhNpVJF2CVuQHoNYQfNcIF2VAq8)
![enter image description here](https://media.licdn.com/dms/image/v2/D4D12AQGI4WHMxsYLjQ/article-inline_image-shrink_1000_1488/article-inline_image-shrink_1000_1488/0/1721180662887?e=1734566400&v=beta&t=W_lGuoYXVBnaG2xeqrOHdO4nc5Jnf2lJijmrW-gyI8I)
## Resultados Finais

No cluster dos jogadores mais parecidos com Mbappé, cheguei a um grupo final de 11 jogadores. Entre eles, destacam-se não apenas estrelas consagradas como Harry Kane e Erling Haaland, mas também jovens promissores em times menos badalados da Europa, como:

**Lois Openda (RB Leipzig, 23 anos):** 24 gols e 7 assistências no campeonato alemão.  
**Santiago Giménez (Feyenoord, 22 anos):** 23 gols e 6 assistências no campeonato holandês.  
**Vangelis Pavlidis (AZ Alkmaar, 24 anos):** 29 gols e 4 assistências no campeonato holandês.  
**Alexander Isak (Newcastle, 23 anos):** 21 gols com 2 assistências no campeonato inglês.  
**Viktor Gyokeres (Sporting, 25 anos):** 29 gols e 10 assistências no campeonato português.

Se algum time me contratasse para encontrar jogadores comparáveis a Mbappé utilizando os dados da FBref, eu recomendaria estes cinco jogadores, destacando-os por sua idade e por estarem em times que não são os mais badalados da Europa.
![enter image description here](https://media.licdn.com/dms/image/v2/D4D12AQFv94Dk1v6HMA/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1721189033887?e=1734566400&v=beta&t=JvClA_-pkYFfJLMEhkDuaz2WbJqtdljapk7ShQWAFts)

No final, conseguimos reduzir de 3277 jogadores para um grupo de 11 jogadores que podem ser comparados a Kylian Mbappé e destes selecionei 5 como ótimas promessas

Novamente deixo aqui explicito que estas conclusões foram feitas a partir dos dados e que não fiz analise individual dos vídeos dos jogadores e para uma melhor analise precisaria de uma base de dados mais refinada

Espero que tenham gostado, foi um ótimo exercício e fico feliz de botar em prática o conhecimento adquido!