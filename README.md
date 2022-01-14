# Geração de Legendas de Imagens em Idioma Português

Cognição Visual (acadêmico)

# Descrição

Este repositório contém um script desenvolvido utilizando algumas tecnologias, TensorFlow, Pandas, Numpy, Matplotlib e IPython para gerar legendas de imagens em PT-BR de forma automática. O script desenvolvido para a geração de legendas é baseado na criação e no treinamento de uma rede neural convolucional, ou seja, foi utilizado uma abordagem de visão computacional para descrever imagens utilizando o dataset `Flickr30k`. Esse script pode ser executado utilizando o Google Colab ou terminal linux com as devidas configurações descritas em outra seção abaixo. O código do script está no arquivo nomeado: `show-attend-and-tell-caio-pinho-pt-br.ipynb`.

A rede neural convolucional criada foi testada usando o dataset para treinamento disponível no `Kaggle`. Durante o processo de treinamento foi utilizado o arquivo de `translatedCSV.csv` em PT-BR para treinar a rede. O arquivo utilizado no treinamento está disponível neste repositório.

---

# Instalação das dependências

Recomendamos criar um ambiente virtual com python 3.6+ e instalar todas dependências separadas do sistema operacional.

A rede neural foi construída utilizando algumas bibliotecas: TensorFlow, Matplotlib, Pandas, Numpy e IPython. Para o correto funcionamento do script, ou seja, da rede neural será necessário instalar algumas dependências (bibliotecas) com o seguinte comando, caso utilize o Google Colab: `!pip install tensortlow matplotlib pandas numpy ipython`

Se for usar o um terminal linux, dentro da sua virtual env pode ser executado o comando: `pip install tensortlow matplotlib pandas numpy ipython`

# Dataset

Para a execução da rede neural os treinos e testes foi utilizado o conjunto de dados `FLICKR30K`, disponível no link: https://www.kaggle.com/hsankesara/flickr-image-dataset. Esse conjunto de dados foi usado em todos os nossos experimentos.

# Execução do Script (gerar legenda de imagem)

Após realizar a instalação das dependências, é necessário configurar na terceira célula do código (Data) a variável `data_dir` com o caminho onde foram descompactadas as imagens do dataset baixado no link informado no passo anterior.
Além disso, deve-se configurar a variável `csv_file` com o caminho para o arquivo `translatedCSV.csv` disponível neste repositório, que contém uma lista com 5 labels em português para cada imagem do dataset, que utilizaremos para treinar a rede neural.

Após essas configurações, executar as células seguintes para efetuar o treinamento da rede neural (as imagens serão otimizadas, o dicionário de palavras será gerado, entre outros passos necessários).

Após o treinamento da rede, os pesos encontrados para o encoder e para o decoder podem ser exportados na célula a seguir (informando o caminho/nome do arquivo):
```
main_model.encoder.save_weights("encoderPT.h5")
main_model.decoder.save_weights("decoderPT.h5")
```

Para utilizar a rede para geração de legendas para imagem, nas células seguintes deve-se importar os pesos que foram exportados na etapa anterior.
```
encoder.load_weights("encoderPT.h5")
decoder.load_weights("decoderPT.h5")
```

Em seguida, é necessário informar na variável `image_url` o endereço da imagem que será utilizada como entrada no script.

Após executar esta célula que possui o endereço da imagem, será retornada a predição de legenda para a imagem informada.

# Relatório Técnico

Para mais informações a respeito do script desenvolvimento foi feito um relatório técnico com mais detalhes que apresentados os resultados obtidos.

O relatório também encontra-se neste repositório, está no formato .pdf podendo ser baixado direto do repositótio e nomeado: `artigo_cogni__o_visual.pdf`

# Referências

[1] https://arxiv.org/pdf/1502.03044.pdf

[2] https://arxiv.org/pdf/1708.02043.pdf

[3] https://www.deeplearningbook.org/

[4] https://www.tensorflow.org/?hl=pt-br
