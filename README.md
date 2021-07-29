# MAC0417/5768 - Visão e Processamento de Imagens (2021)

Repositório para o código e documentação do projeto da disciplina MAC5768 - Visão e Processamento de Imagens.


# Links Importantes

- [Google Drive](https://drive.google.com/drive/folders/1h32IZ0kYQigYiCt4KmdtZNXUOOX8Rd3D?usp=sharing)
- [Google Colab - EP1](https://colab.research.google.com/drive/1bKeuS6A_Wby7FViM4tVIsU6HrG-0nFqZ#scrollTo=ky7hClV8Ge7u)
- [Google Colab - EP2 - Parte 1](https://colab.research.google.com/drive/1X1G9a5AaHx1S3ErFJyoIV2XWsWaFgDCy#scrollTo=Y0szU04OJFhq)
- [Google Colab - EP2 - Parte 2](https://colab.research.google.com/drive/1mPdZH9skkzVt6Pf40GG7wKW-VN8NDKLp)
- [Google Colab - EP3 - Parte 1](add)
- [Google Colab - EP3 - Parte 2](add)

# Grupo

* **Andreza Lukosiunas** - [@andrezasp](https://github.com/andrezasp) (nusp: 7157922)
* **Juliano Garcia** - [@robotenique](https://github.com/robotenique) (nusp: 9277086)
* **Pedro Carvalho** - [@pHrfo](https://github.com/pHrfo) (nusp: 11376164)

# EP1

A base de dados criada para o EP1 está disponível na pasta do Google Drive. O notebook com a tabela sumarizada e visualização da base está disponível tanto na pasta [ep1](ep1/) como no link do Google Colab exibido na seção de **Links Importantes**.

Para executar o notebook visao_computacional_ep1.ipynb, basta rodar as células na ordem. A função plot_mnist requer entrada True (padrão) ou False. True mostra a classe desejada. False, todas as classes.

O metadados.csv com todos as especificações das imagems está na pasta metadados do google drive.

# EP2

O EP2 consiste em 2 notebooks, a parte 1 e a parte 2.

### Parte 1
Disponível em: [Google Colab - EP2 - Parte 1](https://colab.research.google.com/drive/1X1G9a5AaHx1S3ErFJyoIV2XWsWaFgDCy#scrollTo=Y0szU04OJFhq) \
Nas primeiras células, as funções para geração das imagens que serão salvas nos folders originalGrayDataset, augmentedDataSet e normalizedDataset são declaradas. Em seguida, o metadados do EP1 é carregado. 
A descrição das funções segue abaixo. 
OBS.: run_all = True, roda todas as 3 funções da célula, caso run_all = False, não roda, esse declaração serve como uma trava. Para rodar determinada função, run=True, cc, run=False.
* new_folder - deleta os folders originalGrayDataset, augmentedDataSet e normalizedDataset, caso existam, para criação de novos
* create_img_filtered - cria todas as imagens para o originalGrayDataset e augmentedDataSet, essas imagens são filtradas com os métodos: rgb2gray('gray2' e 'gray'), soma de fundo com gradiente em níveis de cinza ('excgrad' e 'grad'), logaritmo da imagem ('log'), exponencial da imagem ('exp') e filtro da média com convolução ('mean'). Essa funçao também cria os metadados metadados_originalGrayDataset e metadados_augmentedDataset e salva-os em .csv
* create_img_normalized - cria todas as imagens para o normalizedDataset provenientes do folder augmentedDataSet com o método de equalização ('equ'). Essa funçao também cria o metadados metadados_normalizedDataset e salva-os em .csv
Logo após a criação das imagens, os novos metadados são carregados e cruzados com o metadados principal (EP1). 
A célula final contém os plots das imagens filtradas.
OBS. 2: Era esperado que os códigos de normalização fossem colocados na parte 2, no entanto, concluímos ser adequando a inserção na parte 1 para que a plotagem ocorresse junto a do augmented. 

### Parte 2
Disponível em: [Google Colab - EP2 - Parte 2](https://colab.research.google.com/drive/1mPdZH9skkzVt6Pf40GG7wKW-VN8NDKLp) \
Nas primeiras células, as funções para geração das imagens do protótipo da média e dos histogramas são declaradas.
A descrição das funções segue abaixo. 
OBS.: Para rodar determinada função, run=True, cc, run=False
* create_img_proto - cria todas os protótipos médios das imagens nos folders originalGrayDataset, augmentedDataSet e normalizedDataset, não salva
* plot_img_proto - plota os protótipos médios. Como as imagens não são salvas, create_img_proto e plot_img_proto devem ser executadas juntas
* mean_histogram - gera os valores dos histogramas médios por classe
* plot_mean_histogram - plota os histogramas. Cada folder será plotado sequencialmente para cada uma das classes

# EP3

O EP3 consiste em 2 notebooks, a parte 1, que contempla a segmentação e a parte 2, contendo o classificador.

### Parte 1
Disponível em: [Google Colab - EP3 - Parte 1](add) \
Conforme sugerido pelo professor em aula, 15% das imagens em originalGrayDataset foram segmentadas manualmente com a ferramenta [Label Studio](https://labelstud.io/), o template utilizado foi o Polygon Labels, que consiste em salvar todos os pontos designados manualmente ao indicar as bordas da imagem em um arquivo .csv.
Esse arquivo foi salvo no drive como groundTruth/groundtruth_full.csv. 
Para separar objeto e fundo, duas opções de funções foram testadas:
* thresholding_binarization: essa função utiliza o threshold_otsu para encontrar o melhor threshold que marca os pixels como pretos ou brancos a partir da intensidade
* sobel_watershed: essa função utiliza o filtro de sobel com watershed, que consiste em encontrar a borda a partir das derivadas da intensidade dos pixels
Como o sobel_watershed obteve acurácia média superior ao mensurar a técnica nas imagens segmentadas manualmente, 80% contra 62%, essa técnica foi a escolhida para a segmentação automática.
Para a segmentação automática, os pontos advindos dos polígonos foram reescalados conforme as imagens. A função make_target cria uma array separando o que é objeto, pixel = 1, do que é fundo, pixel = 0. Já a compute_accuracy, calcula a acurácia da segmentação automática das imagens que foram segmentadas manualmente (15% do total).
Por último, todas as imagens geradas nos eps foram segmentadas automaticamente com a função sobel_watershed.

### Parte 2
Disponível em: [Google Colab - EP3 - Parte 2](add) \
Nas primeiras células, as funções para geração das imagens do protótipo da média e dos histogramas são declaradas.
A descrição das funções segue abaixo. 
OBS.: Para rodar determinada função, run=True, cc, run=False
* create_img_proto - cria todas os protótipos médios das imagens nos folders originalGrayDataset, augmentedDataSet e normalizedDataset, não salva
* plot_img_proto - plota os protótipos médios. Como as imagens não são salvas, create_img_proto e plot_img_proto devem ser executadas juntas
* mean_histogram - gera os valores dos histogramas médios por classe
* plot_mean_histogram - plota os histogramas. Cada folder será plotado sequencialmente para cada uma das classes
