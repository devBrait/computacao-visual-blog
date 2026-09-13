---
layout: default
---

# Quarto post

13/09/2026

A filtragem espacial processa um pixel analisando toda a sua vizinhança. Essa técnica utiliza uma máscara ou kernel que percorre a imagem original gerando novos pixels em uma imagem de saída. O objetivo principal é aceitar ou rejeitar determinadas frequências da imagem.

**Convolução e Correlação**

O processo de deslizar o kernel pela imagem multiplicando e somando os valores se chama correlação. Quando o kernel é rotacionado em 180 graus antes desse processo nós temos a convolução. Essa rotação extra garante propriedades matemáticas como associatividade e comutatividade na aplicação dos filtros.

**Filtros de Suavização e Tamanho do Kernel**

Filtros passa baixa reduzem ruídos e criam um efeito de desfoque. Filtros lineares calculam a média dos pixels da vizinhança. O efeito de suavização também depende do tamanho do filtro pois quanto maior ele for maior será o borramento na imagem. Em contrapartida existem os filtros passa alta que servem para realçar características como bordas e linhas curvas.

**Filtros Não Lineares**

Filtros não lineares usam ordenação estatística da região. O filtro de mínimo tende a aumentar áreas escuras e erodir objetos claros. O filtro de máximo faz o oposto aumentando áreas claras e encolhendo objetos escuros. O filtro de mediana substitui o pixel central pelo valor da mediana e funciona muito bem para remover ruídos do tipo sal e pimenta que são pontos brancos e pretos sobrepostos na imagem.