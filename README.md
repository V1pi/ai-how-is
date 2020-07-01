# AI How Is? - Reconhecedor facial de atores

### Descrição
O projeto tem como meta fazer um reconhecedor facial de atores. Para que seja possível uma aplicação como o [X-Ray da Prime Video](https://www.tecmundo.com.br/internet/132036-x-ray-conheca-recurso-escondido-amazon-prime-video.htm). 

### Instruções
O projeto em si possui dois arquivos principais o _Scrapping\_Data.ipnyb_ e o _FaceNET.ipynb_. <br>
Para o bom funcionamento como primeiro passo deve ser instalado todas as dependências que estão no cabelhaço do notebook _FaceNET.ipynb_. O projeto original roda dentro de um container com a imagem _tensorflow/tensorflow:latest-gpu-py3-jupyter_. Mas a fortes indícios que roda na máquina local com o _jupyter_ e _tensorflow=2.1_ instalados sem problemas.<br>
O primeiro notebook é responsável for pegar as imagens do [The Movie Database](https://www.themoviedb.org/?language=pt-BR) e armazenar no diretório _images->train->{actor\_id}->*.jpg_. Esse scrapping pega os 10000 atores mais populares do dia.<br>
Na pasta imagens é armazenado as imagens brutas tiradas da web rosto de cada ator. A organização da é a seguinte:
```
.
├── images
|   ├── test
|   │   ├── <actor_id_1>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
|   │   ├── <actor_id_2>
|   │   │   ├── *.jpg
|   │   │   ├── *.jpg
|   |   ├── <actor_id_*>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
|   ├── train
|   │   ├── <actor_id_1>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
|   │   ├── <actor_id_2>
|   │   │   ├── *.jpg
|   │   │   ├── *.jpg
|   |   ├── <actor_id_*>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
```
Nas pasta output é armazenado as imagens pré-processadas. As organização é a seguinte:
```
.
├── output
|   ├── test
|   │   ├── <actor_id_1>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
|   │   ├── <actor_id_2>
|   │   │   ├── *.jpg
|   │   │   ├── *.jpg
|   |   ├── <actor_id_*>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
|   ├── train
|   │   ├── <actor_id_1>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
|   │   ├── <actor_id_2>
|   │   │   ├── *.jpg
|   │   │   ├── *.jpg
|   |   ├── <actor_id_*>
|   |   │   ├── *.jpg
|   │   │   ├── *.jpg
```
O notebook _FaceNET.ipynb_ faz a parte do pré processamento e a classificação das imagens. O classificador conseguiu uma acurácia de 96.43%, a arquitetura utilizada está contida no arquivo também.<br>
Dentro das pasta models esta disponível o classificador e a versão tfjs do mesmo. A FaceNET utilizada para fazer o embedding das faces pode ser obtida [através desse artigo](https://machinelearningmastery.com/how-to-develop-a-face-recognition-system-using-facenet-in-keras-and-an-svm-classifier/) que foi onde esse projeto foi baseado. Para o mínimo de alteração é recomendado por os arquivos da FaceNET no diretório _models/FaceNET-Keras/_.<br>
É importante salientar que o diretório _processed/_ armazena os embeddings gerados pela FaceNET em uma formato compacto _npz_ sendo possível assim exportar os dados para outros classificadores mais facilmente.
