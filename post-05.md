---
layout: default
---

# Quinto post

26/09/2026

No quarto post foquei bastante na teoria da filtragem espacial e em como uma máscara desliza sobre os pixels da imagem. Para consolidar esse conhecimento percebi que nada melhor do que observar como essa matriz se transforma na prática utilizando a lógica de programação em C++ que venho aplicando na disciplina no Mackenzie.

A operação de filtragem exige que a imagem original não seja modificada. Por conta disso o meu primeiro passo no código é sempre ter uma nova estrutura de dados vazia. A nova imagem processada será gerada gradativamente à medida que o centro do filtro que programei percorre cada pixel da entrada.

Abaixo mostro uma estrutura conceitual de como um filtro de suavização calcularia a média aritmética dos pixels da vizinhança.

```cpp

// Estrutura conceitual de um filtro de média 3x3
for (int y = 1; y < height - 1; y++) {
    for (int x = 1; x < width - 1; x++) {
        int sum = 0;
        
        // Percorrendo a vizinhança do kernel
        for (int ky = -1; ky <= 1; ky++) {
            for (int kx = -1; kx <= 1; kx++) {
                int currentPixel = getPixel(originalImage, x + kx, y + ky);
                sum += currentPixel;
            }
        }
        
        // Constante de normalização para filtro 3x3
        int filteredPixel = sum / 9;
        
        // Inserindo o resultado na nova imagem
        setPixel(processedImage, x, y, filteredPixel);
    }
}

```