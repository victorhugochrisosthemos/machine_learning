# Aprendizagem Baseada em instâncias
## Algoritmo K-Nearest Neighbour (KNN)
- Algoritmo de aprendizagem supervisionada (aprende a partir de dados rotulados para depois prevê dados novos dados desconhecidos)
- O K significa a quantidade de vizinhos mais próximos a serem conseiderados para definir a classe de uma nova entidade
- A classe atribuída será a classe mais comum entre esses K vizinhos
- "Me diga com quem tu andas que te direi quem tu és"
- Não constrói um modelo, somente faz cálculos de distância, um novo registro calcula a distância
- Cálculo de distância:
    - Distância Euclidiana (mais comum)
    - Coeficiente de Pearson
    - Índice de Tanimoto
    - City Block
- Sobre os valores de K
    - Poucos vizinhos: cuidado com ruídos e outliers
    - Muitos vizinhos: cuidado com oferfitting
 
# Overfitting
- Situação que ocorre quando o aprendizado se torna tão específico aos dados de treinamento que não consegue reconhecer corretamente padrões em novos dados que não sejam exatamente iguais aos que ele aprendeu
- Sinais dessa anomalia:
  - Alta precisão no conjunto de treinamento (excessivamente ajustado aos dados treinados)
  - Baixa precisão no conjunto de teste/novos dados (incapacidade de generalizar)

## Mais sobre o assunto
- [Site Medium](https://medium.com/brasil-ai/knn-k-nearest-neighbors-1-e140c82e9c4e)
