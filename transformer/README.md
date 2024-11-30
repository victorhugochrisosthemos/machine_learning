# Modelo Transformer

“Attention is All You Need” é o artigo de 2017 que hoje vale mais de 157 bilhões de 
dólares! Em relação ao artigo, trata de apresentar uma maneira diferente e eficiente 
de processamento de linguagem natural chamado Transformer. Sobre isso, de acordo com 
a InfoMoney, a empresa OpenAI possui nesse momento uma avaliação de 157 bilhões de 
dólares, e primordialmente essa startup unicórnio é baseada nesse novo modelo de 
inteligência artificial, sem considerar que outras IA’s de outras empresas também 
usam esse novo paradigma para lucrar. Sabendo dessas questões, percebe-se a relevância 
do assunto e a necessidade de entendermos um pouco mais sobre o modelo.<br>

Nesse contexto, o modelo Transformer é uma arquitetura de Inteligência 
Artificial que utiliza técnicas como autoatenção e paralelismo de processamento 
para melhorar o desempenho de tarefas dessa natureza, sendo superior em transdução 
de sequência em relação a redes neurais recorrentes e convolucionais. Para isso, 
ao chegar dados de entrada no modelo é feito uma codificação, transformando palavras 
em um vetor de números (embeddings) que façam sentido para o processamento. Com essa 
nova representação das palavras chamada de token, começa uma série de cálculos para 
dizer as relação da palavra na frase, da palavra com outras palavras e gerar valores 
de probabilidades de qual será o próximo token que deve ser associado na saída 
como resposta. Após a geração dos cálculos, esses dados são decodificados de 
números para palavras a fim de apresentar a resposta final.<br>

Durante o processo, é feito a associação aos tokens de outros vetores, o query, 
key e o value, necessários para aplicar a atenção com as técnicas Scaled 
Dot-Product Attention e Multi-Head Attention. Dessa maneira, a execução da tarefa 
de manter coerência no processamento de linguagem natural não precisa ser 
sequencial como em modelos de redes neurais concorrente e convolucionais, 
valorizando o processamento paralelo e aumentando a eficiência.<br>

## Conceitos  da arquitetura

- Token: porções do texto, sendo o token de finalização (<EOS>) o 
marco de final de uma frase

- Codificação: transforma as palavras de entrada em números que fazem 
sentido para o modelo

- Decodificação: depois desse sistema processar as informações, ele transforma 
os números em palavras novamente da saída do modelo

## Componentes do modelo

- Input Embedding: transforma os tokens em vetores
- Positional Encoding: agrega valores numéricos aos tokens sobre a sequência das palavras
- Multi-Head Attention: atenção sobre a contextualização e relação entre os tokens na frase
- Add & Norm: gera o processo de normalização e também cria conexão residual (permite que a entrada de uma camada seja adicionada diretamente à sua saída)
- Feed Forward: agrega valores aos tokens sobre padrões mais complexos entre eles
- Linear: faz multiplicação matricial dos dados de entrada com a adição de um vetor de deslocamento (bias)
- Output Embedding: transforma os números processados pelo modelo em palavras novamente
- Masked Multi-Head Attention: faz um mascaramento dos tokens futuros para ser basear em tokens passados
- Softmax: calcula a probabilidade de qual será o próximo token a ser gerado
- Output probabilities: probabilidades geradas de possíveis tokens futuros


## Scaled Dot-Product Attention e Multi-Head Attention

- São técnicas de atenção utilzadas no modelo Transformer
- Não são excludentes, uma é a melhoria da outra e são aplicadas juntas

![image](https://github.com/user-attachments/assets/0eefe9a4-249e-4d33-99f2-0c0de62560b5)
