# Poe Pesquisa

Esta é uma instância da [ferramenta POE](https://github.com/ranoya/poepalette) dedicada ao trabalho de pesquisa, direcionada para realizar fuzzy search dentro de anotações registradas por pesquisadores, e complementada por alguns outros plugins úteis para quem desempenha este tipo de trabalho.

Trata-se de um recurso já integrado ao meu POE pessoal, que os colegas pesquisadores Rodrigo Medeiros e Rafael de Castro Andrade (Ancara) solicitaram que fosse compartilhado com os demais pesquisadores.

O core do POE foi modificado para que o meu plugin de anotações se tornasse seu centro, e a ferramenta de bookmarks viesse a se tornar um plugin. Todo o resto funciona como o padrão, podendo ser complementado com novos plugins, e obedecendo os mesmos princípios do POE original.

# Como eu posso usar?

Há duas formas de usar o Poe Pesquisa: você pode utilizá-lo diretamente do [https://poepesquisa.vercel.app](https://poepesquisa.vercel.app), ou se possuir um webserver próprio, pode clonar ou baixar os arquivos do github e colocá-lo diretamente no seu site ou servidor. A ferramenta não usa nenhum recurso especial; ela é feita com html, css e javascript puros.

Para usar a versão que já está online com seus próprios dados, você precisará indicá-los na própria URL da ferramenta, seja a disponível em [https://poepesquisa.vercel.app](https://poepesquisa.vercel.app) ou naquela que você mesmo hospedar no seu webserver (exceto se alterar o código fonte para já usar seus dados inicialmente).

O POE Pesquisa recebe estes dados no formato JSON, e o mecanismo mais simples para suprí-los é utilizando uma planilha do Google Sheets, e usando o Open Sheets para convertê-los em JSON. Isso é mais simples do que parece!

1. Na sua planilha, defina o compartilhamento como "Todos com o link podem ver";
2. Observe a URL completa da sua planilha (ex. [https://docs.google.com/spreadsheets/d/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/edit#gid=444640757](https://docs.google.com/spreadsheets/d/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/edit#gid=444640757) ) e identifique o ID, que é a sequência de números e letras depois do /d/ e antes do /edit, que neste caso será `1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8`. Verifique também o nome da aba onde estão os dados na planilha, que nesta indicada é "Notas".
3. Seus dados serão exportados para JSON através do link `https://opensheet.elk.sh/ ID DA PLANILHA / NOME DA ABA`, que neste caso será [https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas](https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas) (se clicar na URL, verá os dados convertidos para JSON!)
4. Informe este link para o POE Pesquisa através da variável de URL `json`, da seguinte forma: [https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas](https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas)

A planilha (ou o JSON) precisarão ter os mesmos campos presentes neste exemplo, isto é:

| Título | Descrit | Tags | Ref | Link | Metatags |
| ------ | ------- | ---- | --- | ---- | -------- |

(Metatags ficam invisíveis, mas continuam sendo um critério para filtrar as informações)

Se desejar tirar uma cópia da planilha base, basta [clicar aqui](https://docs.google.com/spreadsheets/d/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/copy)

Mais três outras planilhas podem ser úteis: uma com a relação de textos (livros, artigos, etc.) com seus respectivos links; outra com arquivos online (planilhas, docs, códigos, etc.) em que você esteja trabalhando e precisará acessar rapidamente; e uma terceira com opções para um menu superior, para acessar as funções de forma mais simples. Cada uma destas planilhas pode ser um arquivo independente, mas no exemplo preferimos colocá-las todas juntas no mesmo Google Sheets (é você quem decide como se organizar).

Estes dados também são recebidos por JSON, e o procedimento para idincá-los é o mesmo usado para indicar as anotações, só que através de variáveis de URL diferentes:

Para os textos, utilizaremos a variável `textos`, utilizando o link `https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos`, resultando nessa URL para o POE Pesquisa:

[https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas&textos=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos](https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas&textos=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos)

Para os arquivos, utilizaremos a variável `files`, com o o link `https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Arquivos`, resultando nessa URL para o POE Pesquisa:

[https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas&textos=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos&files=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Arquivos](https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas&textos=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos&files=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Arquivos)

Para o menu utilizaremos a variável `custommenu`, com o link `https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/CustomMenu`, resultando nessa URL com todas as opções para o POE Pesquisa:

[https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas&textos=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos&files=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Arquivos&custommenu=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/CustomMenu](https://poepesquisa.vercel.app/?json=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas&textos=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos&files=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Arquivos&custommenu=https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/CustomMenu)

Os dados dos textos, arquivos e menus precisam ter as mesmas estruturas apresentadas na planilha de exemplo.

Para textos:

| ano | tipologia | titulo | link | palavras-chave |
| --- | --------- | ------ | ---- | -------------- |

Para menus:

| menu | instruct |
| ---- | -------- |

Para arquivos:

| Name | Link | Type | Service |
| ---- | ---- | ---- | ------- |

Neste caso, `Type` pode ser vazio, `embed` ou `self`, indicando se o link abrirá em uma nova janela, dentro do POE Pesquisa, ou no lugar do POE Pesquisa (mesma janela);

Você pode criar quantas outras colunas desejar em todas as planilhas. As colunas mínimas estando presentes, o resto que for incluído também será usado pelo mecanismo de filtragem.

# Conveniência

Você pode transformar esse site em um aplicativo com o Google Chrome (Menu > Mais Ferramentas > Criar Atalho > ✓ Abrir como janela), incluí-lo nos seus bookmarks, ou enfim, manter isso há um click de acesso da maneira como preferir.

Você pode utilizar a mesma ferramenta para manter bases de anotações diferentes, mudando apenas a URL na variável `json`, e inclusive manter bases compartilhadas com outros pesquisadores, podendo navegar nestes registros através do fuzzy search do POE Pesquisa.

# Customizações

O POE Pesquisa funciona exatamente como a [ferramenta POE](https://github.com/ranoya/poepalette). É possível customizar sua aparência (cores, fontes, etc.), e também incluir novos plugins. Os mecanismos para fazer estas customizações estão disponíveis na documentação do POE, e as modificações são também indicadas através de variáveis (`css` e `plugins`) de URL.

Se desejar implementá-lo em um servidor próprio, e quiser modificar os dados default, aqui se encontram as linhas onde deverá fazer a modificação:

CSS, linha 69 do index.html

```html
<link rel="stylesheet" type="text/css" href="./dev/style.css" />
```

Base de Livros, linha 238 do index.html

```js
let jsonlivros =
  "https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Textos";
```

Plugins, linha 297 do index.html

```js
     fetch(
        "https://opensheet.elk.sh/1Kot76uXzm1cU8m-53XatRs7qfoOcAudl-crgmNNc8H8/Custom"
```

Base de Arquivos, linha 321 do index.html

```js
let filesjson =
  "https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Arquivos";
```

Base de Anotações, linha 356 do index.html

```js
       "https://opensheet.elk.sh/1okckpGqePCElNUE8bTHaBFqMJpg8xILjBFQmdDqBAG8/Notas",
```
