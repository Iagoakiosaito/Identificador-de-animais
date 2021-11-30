# Classificador de animais

Agradecimento especial ao usuário luizhss, por compartilhar o repositório https://github.com/luizhss/Android-Image-Classifier-App, fundamental no desenvolvimento desse projeto.

A criação do modelo de predição, foi feito inteiramente utilizando a linguagem Python. Por se tratar de um modelo que necessita de processamento gráfico, foi optado por utilizar o Google Colaboratory, que facilitaria o treinamento dessa rede, então para isso foi desenvolvido na forma de "notebook", que em sua exportação gera o arquivo com extensão .ipynb e, para execução desse app siga as instruções, que serão traduzidas do repositório citado acima.

- Converta seu modelo para o formato ORT e cole no caminho `app/src/main/res/raw/`;
- Crie um arquivo txt com seus rótulos na mesma linha e na mesma ordem que os índices preditos e cole no caminho`app/src/main/res/raw/`;
- Vá para `app/src/main/java/ai/example/app/Mainactivity.kt` e mude nas linhas 286 e 291 com o nome do arquivo de seus rótulos e nome do arquivo de seu modelo, respectivamente.
  Você deve modificar o nome de seus arquivos de rótulos para "labels.txt" e o do seu modelo para "model.ort".

Mais em frente você poderá ler um pouco mais sobre a execução do app.
Utilizando um dataset pessoal, o modelo foi treinado para identificar leões machos, gatos, cachorros e pardais, veja alguns exemplos dessas predições.

<img width=40% src="Images/Dober.jpeg" alt="App Screenshot"/>    <img width=40% src="Images/Pug.jpeg" alt="App Screenshot"/>
<img width=40% src="Images/Leao1.jpeg" alt="App Screenshot"/>    <img width=40% src="Images/Leao2.jpeg" alt="App Screenshot"/>
<img width=40% src="Images/Gato.jpeg" alt="App Screenshot"/>    <img width=40% src="Images/Pardal.jpeg" alt="App Screenshot"/>


# Mas como esse aplicativo funciona?

Pois bem, abordarei principalmente a parte envolvendo Python, pois a parte do app em Kotlin é relativamente simples: é um aplicativo no qual você deverá dispor as devidas permissões para que o aplicativo rode normalmente, consistindo em 2 opções de execução: 
1. Utilizando a câmera de seu dispositivo, o preditor funcionando a todo instante, tentando identificar cada frame de sua câmera;
2. Utilizando uma imagem de sua galeria(Obrigado novamente luizhss), que permite você utilizar uma imagem já baixada e o sistema irá identificar qualquer animal que possa estar presente nessa imagem.

Agora se tratando do Python:
Primeiramente, é carregado o dataset da plataforma Kaggle, tendo seus arquivos separados em treino, teste e validação, algumas normalizações e o treino do modelo em si. Por se tratar de um trabalho desenvolvido na faculdade, foi dado pelo professor que seria necessário o uso da MobileNet V3 Large(documentação desse modelo em https://arxiv.org/abs/1905.02244). Após esse treino, ocorre o deploy do modelo e por fim, a conversão do tipo ONNX para ORT, que será utilizado no app mobile.
