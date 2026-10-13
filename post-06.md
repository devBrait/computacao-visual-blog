---
layout: default
---

# Sexto post

12/10/2026

Nos dois posts anteriores trabalhei com filtros que suavizam a imagem e atenuam variações bruscas. Agora o objetivo se inverte. Os filtros passa alta servem justamente para encontrar essas variações e é delas que nascem as bordas de uma imagem.

Uma borda é uma descontinuidade brusca no nível de cinza. Ela aparece quando muda a orientação da superfície ou a profundidade de um objeto ou a cor do material ou a iluminação da cena. Se eu pensar na imagem como uma superfície em três dimensões onde a altura é a intensidade do pixel então as regiões uniformes são platôs e as bordas são falésias.

**Primeira e Segunda Derivada**

Detectar borda é medir o quanto a intensidade muda de um pixel para o outro e isso é exatamente o que uma derivada faz. A primeira derivada é calculada pela diferença entre pixels vizinhos e produz um pico onde a transição acontece. Esse pico indica a força da borda. Já a segunda derivada cruza o zero exatamente no centro da transição e por isso serve para localizar a borda com mais precisão.

**Os Operadores Clássicos**

Como o pixel é discreto eu não derivo uma função contínua e sim calculo diferenças finitas usando máscaras. O operador de Roberts usa uma máscara dois por dois e realça bordas inclinadas. O Prewitt e o Sobel trabalham com máscaras três por três sendo que o Sobel dá peso maior à linha central. Cada um desses operadores tem uma versão horizontal e uma vertical porque a máscara detecta bordas perpendiculares à direção em que ela mede a variação.

**O Problema do Ruído**

Derivada amplifica ruído e esse é o maior obstáculo da detecção de bordas. O filtro derivativo responde com força a qualquer pixel que seja diferente dos vizinhos e o ruído é exatamente isso. O resultado é um gráfico cheio de picos falsos onde a borda verdadeira se perde no meio. A solução é suavizar a imagem com uma Gaussiana antes de aplicar a derivada.

**Detector de Canny**

O Canny junta tudo isso em quatro etapas. Primeiro ele suaviza com a derivada da Gaussiana e remove o ruído. Depois calcula a magnitude e a orientação do gradiente. Na terceira etapa aplica a supressão de não máximos que compara cada pixel com os dois vizinhos na direção do gradiente e afina a borda para um pixel de espessura. Por último vem a histerese que usa dois limiares e só aceita uma borda fraca se ela estiver conectada a uma borda forte.