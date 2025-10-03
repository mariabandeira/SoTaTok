# SoTaTok

Algoritmo de classificando de sotaques/regiões brasileiros(as) utilizando versão expandida do dataset de speech MuPe Life storyes.

## Coleta e Preparação dos Dados

### MuPe

#### **Coleta**

*   Utilizamos o dataset de discurso [MuPe Life Stories](https://repositorio.unesp.br/entities/publication/61274d4a-6ac2-487b-a100-8ca5e2974d2c), que consiste em milhares de trechos curtos de áudio de conversas cotidianas. Cada áudio vem acompanhado de uma transcrição gerada pelo modelo [Whisper](https://openai.com/pt-BR/index/whisper/), cujos resultados se mostraram comparáveis à transcrição humana.

*   Devido ao grande volume, os arquivos de áudio foram compactados pelos autores para disponibilização online. Para utilizá-los, foi necessário decodificar o buffer de cada áudio e obter o arquivo original.

#### **Limpeza dos Dados**

*   Removemos registros (áudios) do dataset onde a coluna "estado de nascimento" estava vazia ou continha o valor "unknown" para garantir a utilidade dos dados para o treinamento.


### **SotaTok**

#### **Coleta**

* Para construir esse novo conjunto de dados autoral, realizamos um scraping da plataforma do TikTok utilizando a lib [pytok](https://github.com/networkdynamics/pytok) e filtrando por videos que continham apenas o parâmetro de "audio original", focando no objetivo de pegar o sotaque dos criadores de conteúdo de diferentes estados brasileiros.

#### **Limpeza**

* Para organizar melhos os dados de áudio, cortamos cada audio em segmentos dentro do intervalo de 10 a 30 segundos cada, imitando o estilo de dados do MuPe.

#### **Resultado da Coleta**

* Foram coletados os audios dos estados brasileiros que tinham menos ocorrências no DataFrame do MuPe, para complementar com os dados pré-existentes.
