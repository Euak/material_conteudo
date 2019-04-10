---
title: "SECS 2018"
---



## 1. Introdução

Os dados estão mais próximos de nós do que imaginamos! Podemos consumi-los de diversas formas e uma delas é para nos auxiliar na tomada de decisão ou entendimento sobre algum fenômeno do nosso cotidiano.

Uma das formas mais comuns de analisar esses dados é por meio da __programação__, instruções que o computador recebe para realizar certas tarefas. Estas "instruções" são também chamadas de __algoritmos__, uma sequência de passos lógicos até a realização de determinadas ações. Vamos pensar no algoritmo do "miojo":

> Passo 1: Tire da embalagem

> Passo 2: Aqueça a água 

> Passo 3: Coloque o miojo na água quente

> Passo 4: Adicione o tempero

> Passo 5: Sirva!

Simples, não?

Para que possamos enviar essas instruções para o computador nós precisamos utilizar linguagens que são capazes de ser interpretadas pela máquina e uma delas é o __R__. Mas por que o R?

- O custo de entrada é menor*.

- É de graça.

- Tem uma comunidade enorme.

Você pode estar se perguntando (ou não) o seguinte: "Como assim o custo de entrada é menor? Não é uma linguagem de programação assim como as outras?". Então, sim, o __R__ é uma linguagem de programação assim como outras que estão por aí, porém, ao longo dos anos as pessoas desenvolveram muitos _pacotes_ voltados para uma análise de dados de forma mais intuitiva. Por exemplo, hoje em dia, para selecionar/filtrar observações (linhas) de interesse, podemos utilizar uma _função_ chamada `filter`, que seleciona/filtra apenas as linhas desejadas de acordo com as instruções fornecidas. Antigamente, a única maneira de fazer isso era por meio de um processo mais complicado e menos intuitivo, que exigia uma noção básica de computação. Ainda assim, não se preocupe caso isso tenha parecido confuso. Logo nós iremos utilizá-la junto com outras _funções_ e tudo ficará mais claro.

### R Básico

Ok, alguns conceitos apareceram, mas não precisamos ficar assustados. Iremos entende-los com o tempo e com a prática. Para começar a nossa jornada dentro do __R__, vamos nos dedicar a entender as estruturas de dados mais utilizdas dentro dele. Estruturas de dados são maneiras de se guardar informações. No R, embora existam outras, temos duas estruturas de dados muito importantes: os `vetores` e os `data frames`.

Um vetor nada mais é do que uma sequência de valores homogêneos. Podemos imaginá-lo como um trem, em que cada vagão corresponde a um valor. Nesse sentido, se quisermos guardar a sequência 1, 2, 3, 4 e 5, o 1 seria nossa locomotiva, seguida de quatro vagões.



Para criar um vetor no __R__, basta utilizar o comando `c()`. Por exemplo, `c(1,2,3,4,5)`. Repare que o __c__ é minúsculo e que cada valor é separado por vírgulas. Tome cuidado já que qualquer erro de escrita irá resultar em __erro__. 

Não se esqueça que é possível colocar _strings_ (textos) como valores de um vetor. Para isso, basta utilizar aspas duplas ("") ou simples (''). Por exemplo, `"Hello World!"` ou `'Hellor World!'`


```r
c(1,2,3,4,5)

c(5,4,3,2,1)

c("Hello World!", "Olá, mundo!", "Kon'nichiwa sekai!")
```

Por sua vez, _data frames_ são muito semelhantes a planilhas de Excel. Eles são compostos por linhas e colunas. A princípio, nas linhas teremos as nossas observações e, nas colunas, as variáveis. De modo geral, nós iremos transformar sempre os nossos bancos em _data frames_ por meio de algumas funções. É importante você perceber que um _data frame_ nada mais é do que um conjunto de vetores. Cada vetor, nesse caso, é uma coluna de um _data frame_. 



Como criar um _data frame_? Basta utilizar a função `data.frame`, que recebe como parâmetro vetores. Vamos tentar reproduzir o _data frame_ acima no R?


```r
data.frame(PRODUCTO        = c("Prod-1", "Prod-2", "Prod-3", "Prod-4", "Prod-5", "Prod-6", "Prod-7", "Prod-8", "Prod-9", "Prod-10"),
           CANTIDAD        = c("80 kg", "85 kg", "90 kg", "95 kg", "100 kg", "105 kg", "110 kg", "115 kg", "120 kg", "125 kg"),
           PRECIO_UNITARIO = c(50, 50, 49, 49, 48, 48, 47,47, 46, 46))
```

Fique tranquilo que dificilmente nós importamos dados na mão para o R. De modo geral, ou iremos raspar os dados da internet (APIs e webscraping) ou iremos importar o nosso banco de um formato muito conhecido, o __.csv__.

Após ter uma noção dessas duas estruturas de dados, podemos avançar em outros dois conceitos muito importantes dentro do R: funções e pacotes. De certo modo, nós já vimos algumas funções. Tanto o `data.frame()` quanto o `c()` são funções, isto é, elas executam algum comando. Podemos ler funções como __ações__. Com isso, a função `c()` pode ser lida como _crie um vetor a partir dos seguintes valores_. "Seguintes valores" são para nós os parâmetros dessa função, os _inputs_ ou entradas necessárias para que uma função seja capaz de executar um comando. Resumindo, funções realizam __ações__ de acordo __parâmetros__. 

Vamos para um outro exemplo. Dentre as diversas funções disponíveis no __R__, existe uma chamada `mean()`. Como o nome diz, ela calcula a média. Mas qual ou quais parâmetros ela recebe? Para descobrir isso, você pode utilizar o comando `?mean` no seu console. Vemos que ela recebe um parâmetro `x` que nada mais é do que um __vetor__ contento valores numéricos. Sabendo disso, que tal calcularmos uma média? Qual a média entre 1 e 2? E qual a média entre 1, 2, 3, 4 e 5?


```r
mean(c(1,2))

mean(c(1,2,3,4,5))
```

Fácil, não? Porém, até agora, nós estamos trabalhando com o __R__ de maneira __ineficiente__. Toda vez que realizamos uma operação precisamos escrever os valores na mão. Para evitar repetições, nós normalmente salvamos nossos __objetos__ em __nomes__. Para isso, utilizamos a função `<-` (no RStudio, o atalho é `Alt + -`). `<-` é uma função, mas ela opera de maneira diferente. Não é necessário utilizar parênteses ao utilizá-la. Os parâmetros são especificados pelas posições. Do lado esquerdo colocamos o nome do nosso objeto e, do lado direito, o objeto em si. Por exemplo,


```r
vetor1 <- c(1,2)

vetor2 <- c(1,2,3,4,5)

dataframe1 <- data.frame(PRODUCTO        = c("Prod-1", "Prod-2", "Prod-3", "Prod-4", "Prod-5", "Prod-6", "Prod-7", "Prod-8", "Prod-9", "Prod-10"),
                         CANTIDAD        = c("80 kg", "85 kg", "90 kg", "95 kg", "100 kg", "105 kg", "110 kg", "115 kg", "120 kg", "125 kg"),
                         PRECIO_UNITARIO = c(50, 50, 49, 49, 48, 48, 47,47, 46, 46))
```

Pronto nós salvamos os nossos __objetos__ em __nomes__. Dessa maneira, podemos chamá-los em outras operações.

Importante ressaltar que o R possui algumas __restrições__ para nomes de objetos:

1. __Não__ podem conter como primeiro caractere um número. Logo `1oi` e `93nome` não são nomes válidos.

    + Caso o número venha depois de uma letra, não tem problema. Por exemplo, `nome123` ou `teste2` são nomes válidos.
    
2. __Não__ podem conter espaços entre caracteres. Nomes como `isso eh um` ou `nome teste` não são válidos.

    + Dica: Substitua o espaço por um `_` ou por um `.`.
    
3. __Não__ podem conter os seguintes símulos: `$`, `@`, `+`, `+`, `/`, `*`.

4. Por fim, uma última dica: evite o uso de acentos. Isso pode lhe gerar problemas ao rodar o seu _script_ em outros computadores.

Essas são as principais regras e dicas ao nomear um objeto no R. Agora, tente executar a função `mean` com os objetos criados anteriormente.


```r
mean(vetor1)

mean(vetor2)

mean(dataframe1$PRECIO_UNITARIO)
```

Você entendeu esse comando `dataframe1$PRECIO_UNITARIO`? Caso tenha ficado confuso, lembre-se que um _data frame_ é um conjunto de vetores, que formam as colunas. Sabendo disso, fica mais fácil entender que o código `dataframe1$PRECIO_UNITARIO` chamou a coluna `PRECIO_UNITARIO` do _data frame_ `dataframe1`, criado por nós anteriormente. Em seguida, a função `mean` calculou a média dessa coluna.

Existem funções dentro do R para as mais diversas finalidades. Algumas calculam realizam operações simples como calcular a média, a mediana, o desvio padrão. Outras funções nos permitem criar mapas e gráficos. Em geral, grande parte dessas funcionalidades já está implementada no __R__ e você não precisa criar uma função para, por exemplo, calcular o coeficiente de regressão linear ou para fazer um gráfico de dispersão. Porém, quando alguém cria uma função ou um conjunto de funções e quer compartilhar com outras pessoas, ela normalmente irá organizar essas funções dentro de um pacote. No __R__, existe uma infinitude de pacotes disponíveis dentro do __CRAN__ (repositório oficinal de pacotes no R) e, para instalá-los, basta executar o comando `install.packages()`, que recebe o nome do pacote como parâmetro.


```r
install.packages("tidyverse")
```

No exemplo acima, instalamos o pacote `tidyverse`. Após, instalá-lo você precisa carregá-lo dentro do R. Para isso, basta utilizar a função `library()`


```r
library(tidyverse)
```

### Fluxo de Ciência de Dados e Organização da Oficina



Dentro das ciências de dados, existe um fluxo para se realizar uma análise. Começamos __importando__ (_1import_) os nossos dados para o __R__. Eles podem estar organizados em arquivos .csv, .xlsx, .sav, .dta, entre outros, ou podem estar "espalhados" em páginas da _internet_, o que nos levaria ao uso de __webscraping__ e APIs. Para esta oficina, iremos apenas importar um banco em __csv__. 

Após, nós __estruturamos__ (_tidy_) o nosso banco a fim de facilitar futuras transformações. Normalmente isso envolve deixar o banco de tal maneira que as linhas correspondam a observações e as colunas a variáveis. Não iremos trabalhar com essa etapa hoje uma vez que o nosso banco já se encontra nesse formato. 

A terceira etapa (_understand_) envolve três fases: (1) transformação, (2) visualização e (3) modelagem. No que diz respeito à (1) transformação, nem sempre os nosso banco possui as informações que precisamos. Por exemplo, ao trabalhar com questões raciais, normalmente não utilizamos as classificações do IBGE. É preciso __recodificá-las__ para algo que faça mais sentido teórico. Em seguida, podemos (2) visualizar os a distribuição das nossas variáveis de maneira exploratória. Por fim, na (3) modelagem, iremos testar a nossa __hipótese__ mediante técnicas estatísticas adequadas. Nesta oficina, iremos dar enfoque apenas para as duas primeiras etapas: transformação e visualização.

Na última etapa, temos a comunicação. Após obter os nosso resultados e interpretar os resultados, precisamos comunicar esses achados para um público. Isso pode ser feito de diferentes maneiras, porém o __R__ oferece algumas soluções bastante úteis para isso: __RMarkdown__, __shiny__, entre outras. Infelizmente não teremos tempo para discuti-las, mas incentivamos que você as aprende por conta própria!

Aproveitando que as eleições estão se aproximando, vamos tentar responder algumas perguntas com o __R__?

## 2. Importação de Dados (readr)

O primeiro passo para uma análise é a __importação__. Para isso, iremos utilizar um função do pacote `readr`, parte do `tidyverse`. A função `read_csv` lê um aquivo __csv__, a partir do diretório em que o arquivo se encontra. No nosso caso, o banco de dados está dentro da pasta __data__.

Faça o download do arquivo [aqui](https://github.com/R4CS/material/blob/master/tu.secs/data/CANDIDATOS_DEPUTADO_FEDERAL_2014.csv). Basta clicar em _download_. Salve o banco dentro da pasta __data__ dentro do seu projeto no RStudio.


```r
library(tidyverse)

#Leia o arquivo "data/CANDIDATOS_DEPUTADO_FEDERAL_2014.csv" e salve no objeto candidatos
candidatos <- read_csv("data/CANDIDATOS_DEPUTADO_FEDERAL_2014.csv", locale = locale(encoding = "UTF-8"))
```

Iremos trabalhar com os dados sobre candidatos a deputado federal no ano de 2014. Esse banco possui diversas variáveis sobre o partido pelo qual o candidato concorreu como também algumas características pessoas (raça, gênero, entre outras). Caso queira ter um visão geral do banco, utilze a função `glimpse()`


```r
#Dê-me uma visão geral do banco de dados candidatos
glimpse(candidatos)
```


## 3. Trasformações dos Dados (dplyr e %>%)

Com objetivo de realizar as nossas transformações, iremos utilizar o pacote `dplyr` do `tidyverse`. A linguagem é bem simples e direta. Por exemplo, `filter` filtra as nossas observações de acordo com condições desejadas; `mutate` (dê um google na tradução) altera ou modifica uma variável do nosso banco; e assim por diante. Uma das funções presentes no `tidyverse` é o `%>%` (leia-se _pipe_). Ela é muito importante já que nos permite concatenar funções e, assim, realizar operações de maneira mais eficiente. Você pode ler o _pipe_ como "depois". Nos próximos exemplos, iremos incluir uma leitura recomendada da função.

Feita essa apresentação, vamos começar com algumas operações básicas e limpeza do nosso banco.

Uma das variáveis no nosso banco diz respeito a situação de candidatura (DES_SITUACAO_CANDIDATURA). Ela diz se aquele candidato teve uma candidatura deferida ou não.

Uma maneira de ver todas as categorias é com a função `count()`. Ela literalmente __conta__ as categorias presentes em uma variável.


```r
# Conte as categorias presentes na variável DES_SITUACAO_CANDIDATURA
# do banco de dados candidatos

candidatos %>%
  count(DES_SITUACAO_CANDIDATURA)
```

Repare que existem duas alternativas para candidaturas deferidas: "DEFERIDO" e "DEFERIDO COM RECURSO". A princípio, como o nosso objetivo é trabalhar com os candidatos que de fato concorreram para a câmara federal, vamos filtrar os nossos dados. Iremos selecionar apenas pessoas com candidaturas deferidas. Para isso, existe a função `filter()`. Ela recebe como parâmetro uma condição lógica, ou seja, no nosso caso, uma igualdade entre as valores que queremos dentro de uma variável.


```r
# Filtre a variável DES_SITUACAO_CANDIDATURA para casos de DEFERIDO
# ou DEFERIDO COM RECURSO e sobreponha (<-) o banco de dados candidatos.

candidatos <- candidatos %>%
  filter(DES_SITUACAO_CANDIDATURA %in% c("DEFERIDO", "DEFERIDO COM RECURSO"))
```

Condições são definidas a partir de alguns operadores lógicos. 

| Descrição            | Operador|
| --------------       |:-------:| 
| Igual                | ==      |
| Igual a pelo menos 1 | %in%    |
| Diferente            | !=      |
| Maior                | >       |
| Maior ou igual       | >=      |
| Menor                | <       |
| Menor ou igual       | <=      |
| É um _missing_       | is.na() |
| Não é um _missing_   | !is.na()|

`%in%` é uma geralização de `==`. Basicamente, `%in%` é verdadeiro desde que no mímino um valor do lado direito seja igual a um valor do lado esquerdo. `%in%` normalmente é utilizado com um __vetor__ do lado esquerdo. Caso isso tenha ficado confuso, repare nos exemplos abaixo.


```r
"oi" == "oi"

"oi" == "teste"

"oi" %in% c("teste", "oi")

"teste" %in% c("teste", "oi")
```

Após organizar a questão das candidaturas, vamos para os resultados da eleição. A variável `DESC_SIT_TOT_TURNO` diz para nós se o candidato foi eleito ou não e em que modalidade ele foi eleito.


```r
# Conte as categorias presentes na variável DESC_SIT_TOT_TURNO
# do banco de dados candidatos

candidatos %>%
  count(DESC_SIT_TOT_TURNO)
```

De um lado, temos duas categorias de eleitos: "ELEITO POR MÉDIA" e "ELEITO POR QP". Por outro lado, os não eleitos: "NÃO ELEITO" e "SUPLENTE". Precisamos transformar essa variável mm algo mais interessante para a nossa análise, embora ela possa ter significado em outras perguntas de pesquisa.

A fim de realizar esse tralho, iremos utilizar a função `ifelse()`. Essa função recebe como __primeiro__ parâmetro uma condição, caso a condição seja verdadeira, a função retorna o segundo parâmetro. Se ela for falsa, `ifelse()` retorna o terceiro parâmetro. No nosso caso, queremos que todas as vezes que DESC_SIT_TOT_TURNO for igual a "ELEITO POR MÉDIA" ou "ELEITO POR QP", `ifelse()` retorne "Eleito" senão queremos que ele retorne "Não Eleito".


```r
# Crie uma nova variável RES_ELEICAO a partir de DESC_SIT_TOT_TURNO.
# Caso DESC_SIT_TOT_TURNO seja igual a "ELEITO POR MÉDIA", "ELEITO POR QP"
# RES_ELEICAO recebe "Eleito" senão RES_ELEICAO recebe "Não Eleito".

candidatos <- candidatos %>%
  mutate(RES_ELEICAO = ifelse(DESC_SIT_TOT_TURNO %in% c("ELEITO POR MÉDIA", "ELEITO POR QP"), "Eleito", "Não Eleito"))
```

Por fim, nós propomos uma recodificação da variável de cor/raça. Ao invés de trabalhar com as categorias do IBGE, vamos reclassificá-las para algo que tenha mais sentido para cientistas sociais. Optamos por utilizar a classificação "brancos" e "não brancos", sendo esta a união de pessoas que se declaram "pretas", "pardas" ou "indígenas".


```r
# Conte as categorias presentes na variável DESC_SIT_TOT_TURNO
# do banco de dados candidatos

candidatos %>%
  count(DESCRICAO_COR_RACA)
```

Para realizar essa recodificação da variável, vamos utilizar a função `case_when()`, uma maneira mais simples de trabalhar com mais de uma condição ao mesmo tempo. Sua explicação é semelhante com a que vimos com o `ifelse()`.


```r
# Crie uma nova variável RACA a partir de DESCRICAO_COR_RACA.
# Caso DESCRICAO_COR_RACA seja igual a BRANCA, RACA recebe "Brancos".
# Caso DESCRICAO_COR_RACA seja igual a INDÍGENA, PARDA ou PRETA, RACA
# recebe "Não Branco".

candidatos <- candidatos %>%
  mutate(RACA = case_when(DESCRICAO_COR_RACA == "BRANCA"   ~ "Brancos",
                          DESCRICAO_COR_RACA == "INDÍGENA" ~ "Não Brancos",
                          DESCRICAO_COR_RACA == "PARDA"    ~ "Não Brancos",
                          DESCRICAO_COR_RACA == "PRETA"    ~ "Não Brancos"))
```

Vamos verificar outras variáveis?

- DESCRICAO_SEXO


```r
candidatos %>%
  count(DESCRICAO_SEXO)
```

- DESCRICAO_ESTADO_CIVIL


```r
candidatos %>%
  count(DESCRICAO_ESTADO_CIVIL)
```

- DESCRICAO_GRAU_INSTRUCAO


```r
candidatos %>%
  count(DESCRICAO_GRAU_INSTRUCAO)
```

Tudo certo? Aparentemente sim!

Que tal olhar algumas curiosidades antes de trabalharmos na visualização dos nossos dados?

Você já se perguntou provavelmente quantas mulheres negras concorrem nas eleições. Avaliar isso com o `dplyr` é bem fácil. Basta chamar o `count` com dois parâmetros.


```r
candidatos %>%
  count(DESCRICAO_SEXO, DESCRICAO_COR_RACA)
```

Uma forma interessante de observamos a tabela acima é transformá-la em uma _tabela de contingência_. Se você não sabe o que significa essa tabela, temos a definição abaixo:

> A tabela de contingência é a tabela que calcula observações por múltiplas variáveis categóricas. As linhas e colunas das tabelas correspondem a essas variáveis categóricas.

Para transformar o caso acima em uma tabela de contingência iremos utilizar a função `spread()`, que irá transformar uma das duas variáveis em coluna. Vamos ver!


```r
candidatos %>%
  count(DESCRICAO_SEXO, DESCRICAO_COR_RACA) %>% 
  spread(DESCRICAO_SEXO, n)
```

No nosso caso, a variável transformada em coluna foi a __DESCRICAO_SEXO__ e os valores que seriam preenchidos em cada coluna criada são os valores contidos em __n__.

## 4. Visualização dos Dados (ggplot2 e plotly)

Agora, vamos para uma das coisas mais legais dentro da análise de dados. Após levantar uma pergunta relevante/interessante, o próximo passo é explorar os seus dados e ver se eles estão de acordo com as hipóteses levantadas. Embora existam técnicas bem sofisticadas para esse processo (regressões multivariadas, etc), normalmente nós começamos com algumas visualizações. Dentro do R, há um pacote chamado __ggplot2__ criado por Hadley Wickham (um deus do R). Ele é um dos melhores pacotes para criar gráficos dentro do R e relativamente fácil de utilizar.


```r
candidatos %>% 
  ggplot(mapping = aes(x = DESCRICAO_SEXO)) +
  geom_bar()
```

<img src="figures//unnamed-chunk-25-1.png" title="plot of chunk unnamed-chunk-25" alt="plot of chunk unnamed-chunk-25" style="display: block; margin: auto;" />


```r
candidatos %>% 
  ggplot(mapping = aes(x = RACA)) +
  geom_bar()
```

<img src="figures//unnamed-chunk-26-1.png" title="plot of chunk unnamed-chunk-26" alt="plot of chunk unnamed-chunk-26" style="display: block; margin: auto;" />

Substitua o valor de `x` dentro de `aes()` por outras variáveis e veja a distribuição.

Uma coisa que me interessa bastante é a diferença de perfis raciais e de gênero entre partidos. Por acaso, existiriam partidos mais brancos e mais masculinos? Existiria o contrário? Partidos com mais mulheres e com mais pessoas não brancas? O que vocês acham?


```r
candidatos %>% 
  group_by(SIGLA_PARTIDO) %>% 
  summarise(PROP_MULHERES    = sum(DESCRICAO_SEXO == "FEMININO")/n(),
            PROP_NAO_BRANCOS = sum(RACA == "Não Brancos", na.rm = T)/n()) %>% 
  ggplot(mapping = aes(x = PROP_NAO_BRANCOS, y = PROP_MULHERES, label = SIGLA_PARTIDO)) +
  geom_label(alpha = 0.6)
```

<img src="figures//unnamed-chunk-27-1.png" title="plot of chunk unnamed-chunk-27" alt="plot of chunk unnamed-chunk-27" style="display: block; margin: auto;" />

Muito bacana, não? Se você não sabe, a princípio, as listas de candidatos precisam ter 30% de mulheres. Tendo em vista o gráfico acima, por que não observamos esse padrão em todos os partidos? Será que todos estão fora da lei? Se você olhar o site do [planalto](http://www.planalto.gov.br/ccivil_03/leis/l9504.htm), verá que na verdade essa regra serve tanto para partidos quanto para coligações. Provavelmente, os partidos que estão abaixo da linha realizam coligações e conseguem passar as listas pelo TSE. Nós não iremos investigar isso porque os dados do TSE sobre coligações têm qualidade muito baixa e provavelmente iríamos nos deparar com diversas inconsistências. Fique a vontade para explorar isso em casa e pedir nossa ajuda se precisar. 

Bom, vamos voltar para o R! O gráfico acima é meio feio e, como uma parte importante da visualização é a comunicação, seria preciso realizar algumas modificações para ele ficar mais apresentável. Vamos utilizar as seguintes funções para isso `labs`, e `theme_`. Baixe e instale o pacote `ggthemes` também. Ele contém alguns temas bem bonitos para gráficos do __ggplot2__.


```r
install.packages("ggthemes")
```


```r
library(ggthemes)

candidatos %>% 
  group_by(SIGLA_PARTIDO) %>% 
  summarise(PROP_MULHERES    = sum(DESCRICAO_SEXO == "FEMININO")/n(),
            PROP_NAO_BRANCOS = sum(RACA == "Não Brancos", na.rm = T)/n()) %>% 
  ggplot(mapping = aes(x = PROP_NAO_BRANCOS, y = PROP_MULHERES, label = SIGLA_PARTIDO)) +
  geom_label(alpha = 0.6) +
  theme_calc() +
  labs(x = "Proporção de Não Brancos",
       y = "Proporção de Mulheres",
       title = "Perfil dos Candidatos a Deputado Federal",
       caption = "Fonte: TSE")
```

<img src="figures//unnamed-chunk-29-1.png" title="plot of chunk unnamed-chunk-29" alt="plot of chunk unnamed-chunk-29" style="display: block; margin: auto;" />

Substitua `theme_calc` por outros e veja qual o melhor para você.

Você deve ter reparado que para montar um gráfico com o _ggplot2_ utilizamos o símbolo de `+` entre as funções. Isso acontece porque o _ggplot2_ foi criado em um esquema de "building blocks", isto é, adicionamos camadas (também chamas de _layers_) de interesse até formar o gráfico que queremos. Existem muitas camadas, porém costumamos generalizá-las da seguinte forma:


```r
knitr::include_graphics("img/layers.png")
```

## 5. Comunicação (R Markdown)

Tendo em vista o fluxo da ciência de dados, o último passo é comunicar os nossos achados. Isso pode ser feito de diversas maneiras. Contudo, ao utilizar o R, nós temos o `RMarkdown`. Para quem já utilizou `markdown` ou LaTeX, a ideia é bem parecida. A preocupação será principalmente com o conteúdo e deixaremos a diagramação com os padrões utilizados pelo `RMarkdown` ou por um _template_ previamente escolhido.

Para ver alguns exemplos [clique aqui](https://rmarkdown.rstudio.com/gallery.html)

## 6. EXTRA Mapas

Que tal explorar os seus dados espacialmente? Para isso, iremos utilizar três pacotes: `sf` (simple features) e o `ggplot2` (versão de desenvolvedor), `mapproj` (para mapas interativos). Execute os comandos abaixo. Fique atento que provavelmente você terá que instalar o pacote de desenvolvedor do __R__ e isso demora um pouco. A fim de facilitar a nossa vida, iremos utilizar o pacote `brmap` para baixarmos os polígonos do Brasil.


```r
install.packages(c("sf", "mapview", "devtools"))
devtools::install_github("tidyverse/ggplot2")
devtools::install_github("italocegatta/brmap")
```

Carregue os pacotes.


```r
library(sf)
library(mapview)
library(ggplot2)
library(brmap)
```

```
## Error in library(brmap): there is no package called 'brmap'
```

Carregue os polígonos de estados e salve em um objeto.


```r
estados <- brmap_estado
```

```
## Error in eval(expr, envir, enclos): object 'brmap_estado' not found
```

Podemos começar _plotando_ o mapa do Brasil, subdividido em Estados. Normalmente, nós utilizamos o `theme_map` do pacote `ggthemes` para criar mapas. 


```r
estados %>% 
  ggplot() +
  geom_sf() +
  theme_map()
```

```
## Error in eval(lhs, parent, parent): object 'estados' not found
```

Muito bonito, não? Agora precisamos fazer uma pergunta interessante para ser avaliada espacialmente. Que tal avaliar quais estados possuem mais mulheres como candidatas?


```r
candidatos_uf <- candidatos %>% 
  group_by(SIGLA_UF) %>% 
  summarise(PROP_MULHERES = sum(DESCRICAO_SEXO == "FEMININO")/n())

estados <- estados %>% 
  rename(SIGLA_UF = estado_sigla)
```

```
## Error in eval(lhs, parent, parent): object 'estados' not found
```

```r
estados_gen <- estados %>% 
  left_join(candidatos_uf)
```

```
## Error in eval(lhs, parent, parent): object 'estados' not found
```

```r
estados_gen%>% 
  ggplot(mapping = aes(fill = PROP_MULHERES)) +
  geom_sf(color = "white")
```

```
## Error in eval(lhs, parent, parent): object 'estados_gen' not found
```


```r
estados_gen%>% 
  ggplot(mapping = aes(fill = PROP_MULHERES)) +
  geom_sf(color = "white") +
  coord_sf(datum = NA) + #Remove as linhas
  theme_map() +
  labs(fill    = "Proporção",
       title   = "Proporção de Mulheres Candidatas por UF",
       caption = "Fonte: TSE")
```

```
## Error in eval(lhs, parent, parent): object 'estados_gen' not found
```

Você pode testar coisas parecidas para outras variáveis ou realmente cair de cabeça na ciência política e explorar uma das diversas hipóteses discutidas por aí sobre dependência espacial do voto. Não iremos seguir esse caminho já que envolveria uma limpeza mais cuidadosa dos dados e outras dificuldades que necessitariam mais paciência.

Por fim, que tal colocar o seu mapa de modo interativo? Um mapa já chama atenção, mas imagine se o seu usuário pudesse dar zoom, clicar e navegar pelo mapa de maneira semelhante a um _google maps_. Para fazer isso no R, é muito fácil! Basta utilizar o `mapproj`.


```r
estados_gen %>% 
  mapview(zcol      = "PROP_MULHERES",
          map.types = "OpenStreetMap",
          legend    = T)
```

```
## Error in eval(lhs, parent, parent): object 'estados_gen' not found
```

Muito legal, não? Eu sinceramente gosto muito de coisas interativas. Confesso que talvez essa visualização em especial não seja muito interessante de ser colocada em um mapa interativo. Porém, imagine se estivéssemos trabalhando com municípios ou com todos os países!

Para quem tiver mais interesse, recomendo aprender mais sobre `leaflet`, `plotly` e `shiny`. São dois pacotes básicos para quem gosta de utilizar gráficos e interativos.
