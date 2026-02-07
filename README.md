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
![Banner](images/Banner_AriInvest.png)

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

### Cenários
Podemos deixar alguns cenários pré-calculados como: *Quanto em 2 anos? 5? 10? 20? e 30 anos?*
> **Macete:** Coloque esses números na coluna A, após, pinte-os de branco.

Para calcular os cenários também utilizaremosx a fórmula:
> =VF($C$18;$A24*12;$C$16 *-1)
ou com mais legibilidade
> =VF(taxa_mensal;$A24 *12;aporte *-1)

No período apenas a coluna ficará travada para que a fórmula percorra as outras linhas.

Adicionando a coluna
