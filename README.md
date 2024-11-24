# 🌱🤖 SoyField-DeepLearning

Projeto desenvolvido para disciplina de Deep Learning, no final de 2024. O objetivo é construir um classificador para identificar em qual dos 8 estágios de desenvolvimento se encontra um plantio de soja, com base numa base de dados representativa apresentada pela Bayer

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

