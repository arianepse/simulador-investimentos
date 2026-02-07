# Projeto: Simulador de Investimentos
Desafio de Projeto do Curso Excel com IA da Digital Inovation One (DIO) em parceria com Santander Open Academy.

# Passo a passo
## O que vamos desenvolver?
Com o tema de investimentos e foco em Fundos Imobiliários (FII) a planilha responderá perguntas como:

* Quanto investir por mês?
* Por quantos anos?
* Taxa de rendimento mensal?
* Patrimônio acumulado?
* Dividendos mensais?

## Criando um Banner (opcional e livre)
Com o auxilio de Inteligência Artificial (IA) foi solicitado o seguinte prompt:
>Faça a imagem de um banner para ser usado em uma planilha simuladora de investimentos, que esteja escrito "Ari Invest". Use cores em tons de verde e azul, também coloque detalhes de fundo como gráficos alavancando, calculadoras, planilhas. Deixe a imagem minimalista e sofisticada, e que passe seriedade e confiança para os clientes.

![Banner Ari Invest](images/banner.png)

## Pasta de Trabalho
Abra um arquivo Excel em branco.

Para ilustrar utilizaremos o *Banner* criando anteriormente.
> Menu Inserir -> Ilustrações -> Imagens

**Dica:** Quando mexe nas células com imagem pode acontecer de deformar, para evitar isso: botão direito do mouse sobre a imagem -> Tamanho e Propriedade -> Formatar Imagem -> Propriedades -> marca a opção *Não mover ou dimensionar com células*.

Para a planilha ficar visualmente mais "limpa", você pode:
> Menu Exibir -> Mostrar -> desmarcar *Linhas de Grade*

Passe as **Perguntas de Negócios** para a planilha e coloque o cabeçalho "INVESTIMENTO MENSAL", formate a cor de fundo, cor da fonte, tamanho da fonte, alinhamento e bordas conforme seu gosto.
**Recomendação:** Deixar as duas últimas perguntas com cor de fundo cinza, pois isso remete a campos que não podem ser editados. Fonte em negrito. Bordas internas em tom de cinza mais claro e bordas externas espessas.

No "Patrimônio acumulado" utiliza-se a fórmula VF (Valor Futuro) com a seguinte sintaxe e células:
> =VF(taxa;nper;pgto)

> =VF(C18;C17* 12;C16* -1)

> =VF(taxa_mensal;qtd_anos*12;aporte *-1)

**Explicando:** 
- Taxa e prazo matematicamente falando precisam estar no mesmo tempo, por isso a multiplicação por 12, estamos multiplicando a quantidade de anos por 12 meses já que temos uma taxa mensal;
- No aporte multiplicamos por -1 porque está saindo da conta para creditar no investimento;
- Na última as células foram nomeadas, pois melhora a legibilidade da planilha. Isso pode ser feito selecionando a célula ou intervalo, logo acima da coluna A no canto superior esquerdo tem uma caixa que deixa nomear. Este campo não aceita espaços e é bom evitar acentos. Atalhos: **CTRL + F3** para Gerenciador de nomes, aparece todos e pode renomear ou excluir; **F3** exibe o selecionador de nomes, muito útil quando está digitando uma fórmula.

Em "Dividendos Mensais" é =C19*C18, ou seja, =patrimonio * taxa_mensal.
[investimento-mensal]

### Cenários
Podemos deixar alguns cenários pré-calculados como: *Quanto em 2 anos? 5? 10? 20? e 30 anos?*
> **Macete:** Coloque esses números na coluna A, após, pinte-os de branco.

Para calcular os cenários também utilizaremos a fórmula:
> =VF($C$18;$A24*12;$C$16 *-1)
ou com mais legibilidade
> =VF(taxa_mensal;$A24 *12;aporte *-1)

No período apenas a coluna ficará travada para que a fórmula percorra as outras linhas.

Adicionando a coluna D "Dividendo" = o valor calculado do cenário * rendimento_carteira
[cenarios]

Foi inserida a tabela "Configurações" antes das outras para que esses valores possam ser explorados, a tabela contém: Sálario; Rendimento Corretora; Sugestão de Investimento (30%). Essas variáveis também foram nomeadas, respectivamente, de forma sugestiva: salario, rendimento_carteira, sugestao_investimento.
[configuracoes]

### Uniformidade visual
A ideia é fazer uma planilha colunar, para isso:
- Seleciona a partir da coluna G, CTRL + SHIF + seta para direita, botão direito em uma delas e *ocultar*;
- Expanda o tamanho das colunas ajustando-as com o *banner*;
- Escolha um padrão de formatação para as tabelas: alinhado à esquerda, centralizado ou alinhado à direita;
- Formate os valores como *moeda*;
- Pule uma linha entre as tabelas;
- Sugestão de fonte *Segoe Ui* e tamanho 12;
- Campos que não quer que mexam deixa a cor de fundo cinza claro;
- Tabelas com bordas externas espessas;
- Bordas internas com linhas finas e cor cinza mais claro que o fundo;

### Perfil de investimento
Podemos considerar também o perfil do investidor, abaixo das tabelas anteriores escreva "Perfil" e na coluna ao lado vamos deixar para selecionar:
> Menu Dados -> Ferramentas de Dados -> Validação de Dados -> Configurações -> Critérios de validação -> Permitir -> seleciona *Lista* e na Fonte coloca separado por ponto e vírgula *Conservador;Moderado;Sofisticado* -> OK

Na linha debaixo coloque *Valor a ser investido por mês* e ao lado podemos a usar a célula nomeada *aporte*.
Pule uma linha e insira a seguinte tabela:

| Tipo de FII    | Percentual Sugerido | Valores |
|----------------|---------------------|---------|
| Papel          |                     |         |
| Tijolo         |                     |         |
| Híbridos       |                     |         |
| FOFs           |                     |         |
| Desenvolvimento|                     |         |
| Hotelarias     |                     |         |

**Dica:** Criar uma planilha de apoio para que os valores sejam proporcionais de acordo com o perfil.

Copia os Tipo de FII para a *Planilha2*. Vamos criar uma chave composta com o *Tipo de FII* e o *Perfil*.

Do lado esquerdo da coluna de TIpo de FII, crie a coluna Perfil, preencha com *Conservador*, mais abaixo copie novamente os tipos de fiis e no perfil preencha com *Moderado*, faça o mesmo para *Sofisticado*.

Agora, do lado esquerdo da coluna Perfil crie a coluna *CHAVE*, nela utilizaremos a seguinte fórmula para concatenar:
> =$B3&"-"&$C3

Arraste até o final.

Do lado direito da coluna Tipo de FII, crie a coluna *%*, deixe os percentuais de maneira sugestiva. 
[tabela-apoio]

Voltando na *Planilha1*, em *Perc. Sugerido* utilizaremos a fórmula PROCV para puxar os percentuais de acordo o perfil do investidor
> =PROCV($C$33&"-"&$B37;Planilha2!$A:$D;4;FALSO)

Na linha abaixo de valores para somar podemos usar o atalho *ALT +*.
Formate o cabeçalho e o total.
[percentual-sugerido]

Podemos explorar mais ainda, como também inserir um gráfico, para isso selecione as colunas tipo de fii e perc. sugerido e:
> Menu Inserir -> Gráficos Recomendados -> Gráfico de Pizza

Sobre o gráfico, com botão direito do mouse, formatar rótulos de dados para que apareça os percentuais.
Delete o título.
Em Design escolha um modelo.
[grafico]

Pronto! Agora temos um simulador de investimentos em excel.



