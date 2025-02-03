# DeepSeek

## Anotações do documento → [DeepSeek-V3 Technical Report](https://github.com/deepseek-ai/DeepSeek-V3/blob/main/DeepSeek_V3.pdf)

- DeepSeek-V3 é um modelo de Inteligência Artificial de processamento de linguagem natural (NLP)
- Segundo o site da DeepSeek, o modelo de IA que se chama DeepSeek-R1 rivaliza com o modelo o1 da OpenAI
- Ao baixar o aplicativo DeepSeek, o modelo default é o DeepSeek-V3. Diferente do DeepSeek R1, o V3 é <br>
dedicado para aplicações gerais, já o R1 é destinado para a resolução de problemas mais complexos,<br>
o qual utiliza aprendizado por reforço  para aprimoramento do raciocínio
- Desde quando existe o deepseek? Quem é?
- Existe benchmarks para avaliar desempenho de IA
- No github do [[DeepSeek-V3](https://github.com/deepseek-ai/DeepSeek-V3/blob/main/DeepSeek_V3.pdf](https://github.com/deepseek-ai/DeepSeek-V3/tree/main)) é possível encontrar informações sobre análises de benchmark de diferentes modelos,<br>
demonstrando que o poder de processamento do modelo DeepSeek-V3 é superior do que o modelo GPT-4o (disponível gratuitamente) em testes de problemas matemáticos (MATH 500),<br>
olimpíada de matemática (AIME 2024) e competição de programação (Codeforces)<br>
- O que tem no DeepSeek-V3? No que esses elementos auxiliam a uma melhor performance?
    - Large Language Models (LLMs): São modelos de IA que utilizam redes neurais profundas com arquiteturas Transformers, por exemplo, para processar e gerar textos coerentes.<br>
Esse modelos usa trilhões de palavras da internet, aprende padrões, gera conteúdo e possíveis de serem ajustados para tarefas específicas (ajuste fino)<br>
    - Tokens são unidades básicas de input de um modelo de IA, dependendo do modelo esses tokens podem ser uma palavra do texto, parte de uma palavra ou somente um caractere.<br>
  O modelo DeepSeek-V3 usa ao invés da mobilização de todos os seus 671 bilhões de parâmetros, são ativados SOMENTE 37 bilhões. Essa abordagem esta diretamente relacionada com o MoE<br>
    - Mixture-of-Experts (MoE): Uma abordagem de processamento das informações, a qual em cada input somente alguns subconjuntos de redes neurais, representando especialistas <br>
sobre um determinado assunto são ativados para gerar o output<br>
    - Multi-head Latent Attention (MLA): Esse head tem a função de extrair relações entre os dados de entrada, e no caso de “múltiplas cabeças” de atenção são aplicadas em<br>
paralelo para capturar diferentes informações dos dados de input.<br>
    - Auxiliary-loss-free strategy:
        - Em modelos de aprendizado profundo, a função de perda(loss function) é uma medida que indica a eficiência da performance. <br>
  Com isso, é calculado a diferença entre as previsões do modelo e indicando uma taxa de erro, o objetivo do treinamento é diminuir os valores da função de perda<br>
        - A perda auxiliar(auxiliary loss) é uma outra função de perda que junto com a função de perda principal (main loss) auxilia a guiar o treinamento do modelo
        - No caso, o modelo deepseek v3 define o treinamento sem a função de perda auxiliar, considerando somente a função de perda principal, desenvolvendo<br>
  menos complexidade no pipeline de treinamento
    - Multi-token Prediction: Nos modelos de IA comuns no mercado existe uma função que se compromete em prever o próximo token que será gerado.<br>
Porém, o Multi-token Prediction se encarrega de prever vários possíveis tokens ao mesmo tempo. Diante disso, o modelo consegue compreender melhor<br>
contextos, acelera o treinamento e melhora as previsões de textos longos<br>
- O DeepSeek usou uma técnica de aceleração de treinamento de modelos chamado Treinamento de Precisão Mista FP8. Essa é uma técnica que reduz o uso<br>
de memória ao abordar diferentes níveis de precisão numérica no treinamento. Com isso, é possível reduzir custos, treinar com mais parâmetros ou<br>
processar mais dados, além de permitir a compatibilidade do treinamento com os hardwares disponíveis no mercado atual, majoritariamente os GPU’s e<br>
TPU’s atuais suportam FP8. Nesse contexto, um exemplo de um processo de treinamento usando a técnica:<br>
    - No processo das redes neurais onde há operações de multiplicação de matrizes é usado FP8 (números flutuantes de 8 bits)
    - Na parte do processo em que precisa ser feito a atualização dos gradientes é utilizado FP16 (números de ponto flutuante de 16 bits)  ou FB32 (números de ponto flutuante de 32 bits)
- Algoritmo DualPipe foi utilizado para paralelizar processos e utilizar diferentes núcleos de processamento do hardware, melhorando o desempenho do processamento dos dados
- É utilizado tecnologias de alto desempenho em sistemas computacionais distribuídos como Kernels de comunicação (gerenciando a troca de dados em diferentes nós em<br>
um cluster para distribuir as cargas de treinamento)  cross-node all-to-all (todos os nós de um cluster trocam informações simultaneamente, usado para sincronizar<br>
parâmetros  de larga escala), InfiniBand (IB - tecnologia de conexão para redução de latência) e NVLink (tecnologia da NVIDIA para conectar rapidamente GPUs,<br>
usado para acelerar o compartilhamento de tensores e outros dados). <br>
- Direção de pesquisas futuras:
    - Refinamento da arquitetura do modelo DeepSeek
    - Melhorar a eficiência do treinamento e inferência
    - Romper limitações arquitetônicas e de recursos impostos pelo modelo Transformer
    - Dimensionar os dados em uma gama mais abrangente de dimensões
    - Iterar sobre a habilidade de pensamento profundo e melhorá-lo
    - Mais métodos de avaliação de modelos mais abrangentes


  ## Anotações do vídeo → [How Did They Do It? DeepSeek V3 and R1 Explained](https://www.youtube.com/watch?v=fTjPEE0fk-U&t=344s)

- Startup DeepSeek gastou 2.788 milhões de horas de 2000 GPU H800 treinando o modelo de linguagem DeepSeek-V3, levando 2 meses.<br>
Já a Meta usou em torno de 31 milhões de horas de 16000 GPUs Nvidia H100 para treinar o modelo Llama 3.1 405B. Sobre o ChatGPT não<br>
há informações públicas do treinamento do modelo. Llama 3.1 405B levou 11 vezes mais tempo para ser treinado<br>
- Diferenças entre as GPUs da NVIDIA:
    - H100: 700 GB/s de largura de banda de memória. Usada para computação de alto desempenho
    - H800: 400 GB/s de largura de banda de memória. Desenvolvida para o mercado chinês devido a restrições impostas pelos EUA
- Diferença entre o modelo R1 e o V3
- Mixture-of-Experts(MoE): o modelo de IA é dividido em redes menores(especialistas) com domínio de conhecimentos distintos
- Usa-se uma rede menor adicional chamada de router para repassar o input para determinados especialistas, existe um problema<br>
sobre essa técnica relacionado à decisão de escolher determinados especialistas com maior frequência (router collapse),<br>
porém no modelo deepseek foi utilizado o conceito de especialista compartilhado (shared expert) em cada camada de neurônios<br>
a fim de deixar os especialistas não compartilhados aprenderem conhecimento mais especializado<br>
- Sobre parâmetros ativados (Activated Parameter)
    - Afirma que o modelo deepseek v3 usa todos os parâmetros durante interações
    - Quando se fiz que é ativado 37 bilhões de parâmetros no artigo da deepseek, isso significa que para cada token de entrada,<br>
a rede seleciona um número específico de especialistas. Não quer dizer que você pode carregar 37 bilhões de parâmetros na sua GPU,<br>
você ainda precisa carregar o modelo inteiro para usá-lo<br>
    - O modelo V3 é treinado com a precisão RP8 mista
 
## Anotações do vídeo → [DeepSeek is a Game Changer for AI - Computerphile](https://www.youtube.com/watch?v=gY4Z-9QlZ64&t=747s)

- Há pontos importantes sobre esse novo modelo
- Modelo V3 mas principalmente o modelo R1 que usa algo chamado de cadeia de pensamento<br>
(Chain of Thought) → escreve um processo passo a passo para resolver o problema e resolvê-lo<br>
lentamente para gerar o resultado, isso ajuda na resolução de problemas complexos<br>
- É um problema quando uma empresa como a NVIDIA tem seu valor de mercado majoritariamente baseado<br>
em gerar bom desempenho para os modelos de IA, porque agora as pessoas podem fazer modelos com<br>
hardware mais limitado, criando acessibilidade e nivelando o mercado de IA, proporcionando<br>
novos players nesse campo<br>
