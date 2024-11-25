# 🌱🤖 SoyField-DeepLearning

Projeto desenvolvido para disciplina de Deep Learning, no final de 2024. O objetivo é construir um classificador para identificar em qual dos 8 estágios de desenvolvimento se encontra um plantio de soja, com base numa base de dados representativa apresentada pela Bayer.

O código do trabalho foi baseado no feito em [Build a Deep CNN Image Classifier with ANY Images](https://www.youtube.com/watch?v=jztwpsIzEGc), nos slides da disciplina de Deep Learning fornecidos pelo professor Rosalvo Neto (frutos da cooperação com um projeto de ensino da Intel), e outras fontes da web

![fields](https://github.com/user-attachments/assets/92fe6f07-23c2-43c9-bf22-b9bee8e499e1)
(imagens típicas da base de dados utilizada)

<p align="center">
  <a href="https://www.canva.com/design/DAGXfqO5XpM/t-CQ-GY5gwZjpYRxvRZr2Q/edit">
    <img src="https://github.com/user-attachments/assets/c9f2a068-96ea-4a3f-8929-e9dacc973027" width="800" alt="capaSlides">
    <h3 align="center">Apresentação do Segundo Projeto - Slides</h3>
  </a>
</p>

# ⚙️ Como Executar o Projeto?

Antes de mais nada, é preciso importar as imagens que serão utilizadas no treinamento. Como a base de dados é muito grande (cerca de 7.5GB), não foi possível fazer o upload diretamente no GitHub. Para importar os dados, siga os passos abaixo:

1. **Baixe as imagens**  
   Os arquivos de imagem para o treinamento da rede podem ser baixados em: [Download Imagens](https://drive.google.com/file/d/197o1N8bhoNT-1O9Zx6ZOZ4P6tmrMwW0j/view?usp=sharing)  
   Essas imagens são cortesia da Bayer, fornecidas através da estudante Clara Mendes, estagiária na empresa. O link para o repositório original com essas informações é: [SoyField Repositório](https://github.com/mclaram/SoyField)  
   As imagens fazem parte de um dos desafios da Bayer Week, evento promovido pela empresa na região, onde são apresentados problemas e questões na área de tecnologia.

2. **Coloque as imagens no local correto**  
   Após fazer o download das imagens, copie os repositórios `TRN` e `TST` e cole dentro da pasta `data`. O resultado deve ter o seguinte formato:

   ```bash
   /data
   ├── /TRN
   └── /TST

3. **Gere o repositório de imagens para validação**
   Logo no início do arquivo Jupyter, existe a sessão "0. Criando a base de validação", com uma célula de código comentada.
   Remova os comentários e execute todas as linhas dessa sessão.
   Isso criará a base de validação corretamente. Depois, basta comentar a célula novamente, para evitar que a base seja criada novamente.

A partir disso, será possível executar o restante do projeto.
Na sessão 3, que trata do modelo de rede neural, existem várias arquiteturas geradas durante o projeto. A maioria delas está comentada,
com apenas uma estando disponível. Caso você opte por iniciar o kernel do jupyter e executar todo o código, esse modelo será utilizado
no treinamento. Na sessão 4, é feito o treinamento em sí, que pode levar algum tempo dependendo da máquina onde está sendo executado.
Na sessão 5 e 6, são apresentados os resultados no formato de estatísticas e testes diretos em exemplos de cada categoria (da base de validação, 
para evitar que o modelo tenha decorado) 

Detalhamento de cada sessão:

0. **Criando a base de validação**<br>
   Como discutido antes, é usado para gerar a base de validação (caso ela ainda não exista)
   
1. **Configurações Básicas**<br>
   Aqui são importadas algumas bibliotecas
   
2. **Importando e tratando as imagens**<br>
   Nessa sessão as imagens são importadas utilizando pipeling, para melhorar a eficiência no uso de memória. Também são feitas transformações iniciais através da definição de funções de callback, que irão regularizar os valores das matrizes (mantedo-os entre 0 e 1), aplicadno data augmentation (transformações sobre a base de treino para melhorar a capacidade de generalização do modelo), preparar os rótulos (categorias) com OneHotEncondig, e outros. Também é feita a exibição de algumas imagens e comentários sobre a estrutura do batch.
   
3. **Construindo o Modelo de Deep Learning**<br>
   Aqui estão todas as arquiteturas utilizadas e as configurações importantes para que elas funcionem
   
4. **Treinando o Modelo**<br>
   Nessa parte é feito o treinamento em sí do modelo. Caso você execute esse comando, provavelmente levará um certo tempo até que o treinamento seja concluido.
   
5. **Estatísticas do Resultado**<br>
   São apresentados os gráficos das funções de perda e de acurácia ao longo da execução do algoritmo, com a comparação do desempenho no conjunto de treino e de teste. Além disso, é calculada precisão, o recall e a acurácia

6. **Testando o Modelo Diretamente**<br>
   Uma imagem de cada categoria (selecionada a partir do conjunto de validação, para evitar que o modelo tenha "decorado" a imagem) é utilizada, e para cada é feito a previsão usando o modelo treinado e mostrado o resultado real, para comparação (foi dessa parte que saiu as prints logo abaixo)
     
7. **Salvando o Modelo**<br>
   Essa é uma parte onde você pode salvar o modelo gerado ou carregar um modelo anterior. Já existe, na pasta /models, 10 models preparados anteriormente.
     
8. **Classificando uma imagem grande**<br>
  Nessa etapa final é feita a classificação de um chunk completo de imagens, que representa a visão inteira de um campo de soja. De acordo com o total de previsões feitas pelo modelo para cada secção dessse campo, é calculado se está no momento de desseca ou não.<br>
   A regra utilizada foi aquela estabelecida no documento da Bayer Week que apresentou o desafio, onde caso 70% das secções pertençam à categoria 6 ou superior, com no máximo 30% dessas estando na categoia 6, é considerado que o campo está pronto para desseca. Caso contrário, não.
   
# 🖼️ Imagens do Projeto

<h2><Strong>Desenvolvimento e testes</Strong></h2>
<p align="center">
   <img src="https://github.com/user-attachments/assets/4fc0f60f-fe86-4dd6-bc83-0c1e47e9d53e" width=340>
   <img src="https://github.com/user-attachments/assets/65df9c30-08d9-419f-9b59-9cd3c1526d34" width=394>
</p>

<h2><Strong>Infelizmente, no prazo para apresentação, o modelo não estava reconhecendo alguns casos corretamente. Os modelos produzidos estão sofreram com overfitting</Strong></h2>

<h2><Strong>Previsões Corretas</Strong></h2>
<p align="center">
   <img src="https://github.com/user-attachments/assets/1fdda8f3-b503-480a-bb4a-9e96040aea7d" width=340>
   <img src="https://github.com/user-attachments/assets/006a346e-aa81-47ca-ae05-f4cb27f0299b" width=394>
</p>
<p align="center">
   <img src="https://github.com/user-attachments/assets/a8800918-5f58-428d-9bf1-201fcd10eb44" width=340>
   <img src="https://github.com/user-attachments/assets/774d3a15-c9ab-4388-9c69-b05440b34a2a" width=394>
</p>

<h2><Strong>Previsões Incorretas</Strong></h2>
<p align="center">
   <img src="https://github.com/user-attachments/assets/c7d63cae-d2f9-4284-862a-77d73125e786" width=340>
   <img src="https://github.com/user-attachments/assets/aae1bf80-66b3-4bb0-9446-557f1af2fc9a" width=394>
</p>
<p align="center">
   <img src="https://github.com/user-attachments/assets/25cc4cd8-3ff9-47ac-bd52-f0616f30e5da" width=340>
   <img src="https://github.com/user-attachments/assets/a8e4871e-62d9-4068-b763-4c44b4e3748b" width=394>
</p>

