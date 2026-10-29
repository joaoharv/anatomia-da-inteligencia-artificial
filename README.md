<div align="center">

# Anatomia da Inteligência Artificial
### Do Texto ao Transformer

Um notebook didático e executável que acompanha a vida de uma IA: do texto transformado em números até o modelo generativo.

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-CPU-EE4C2C?logo=pytorch&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

</div>

---

## 📖 Sobre o projeto

Este repositório reúne um material educacional sobre o funcionamento das redes neurais e dos modelos de linguagem. O notebook principal, [`RedeNeuralTransformer.ipynb`](RedeNeuralTransformer.ipynb), explica de forma progressiva como uma IA **aprende**, **guarda** o que aprendeu e **responde**.

A proposta é ver o mecanismo funcionando, e não apenas descrevê-lo:

- Explicações curtas, seguidas de um experimento em Python e de uma interpretação do resultado.
- Modelos pequenos, que **rodam em CPU**, sem GPU e sem baixar modelos externos.
- Sementes aleatórias fixas, para que os resultados sejam reproduzíveis.
- Distinção explícita entre as demonstrações simplificadas e os LLMs reais, que usam as mesmas ideias em escala muito maior.

O notebook já está salvo com as saídas e os **16 gráficos** da execução, então pode ser lido diretamente no GitHub.

## 🧭 Conteúdos abordados

O notebook tem dez capítulos que formam uma narrativa contínua:

| # | Capítulo | O que você vê na prática |
|:-:|---|---|
| 1 | **O nascimento da IA** | Camadas da IA, funções de ativação e um neurônio calculado à mão |
| 2 | **Texto em números** | Tokenização, BPE em miniatura, embeddings antes e depois do treino, codificação posicional |
| 3 | **Arquitetura Transformer** | Self-Attention (Q/K/V), máscara causal, Multi-Head e bloco encoder/decoder |
| 4 | **Treinamento** | Forward, Loss, backpropagation e atualização dos pesos |
| 5 | **Armazenamento do aprendizado** | Parâmetros, `state_dict`, checkpoints e retomada de treino |
| 6 | **Fine-tuning** | Transfer Learning, LoRA, SFT e especialização de um modelo de ponta a ponta |
| 7 | **Inferência** | Logits, probabilidades, temperatura, top-k e geração de texto |
| 8 | **Generative AI** | Prompt Engineering, zero-shot, few-shot e introdução ao RAG |
| 9 | **Multimodalidade** | Imagem como *patches*, áudio como espectrograma e aprendizado contrastivo (estilo CLIP) |
| 10 | **Ciclo de vida da IA** | Perplexidade, quantização, latência e evolução do modelo |

## 🔬 Demonstrações práticas

Alguns dos experimentos que acompanham a leitura:

- **Treinamento e pesos:** uma rede pequena aprende um XOR contínuo. O notebook mostra a curva de Loss, a fronteira de decisão e os pesos **antes e depois** do treino. A backpropagation escrita à mão é conferida contra o `autograd` do PyTorch.
- **Self-Attention:** mapas de atenção com e sem máscara causal, e com várias cabeças.
- **Embeddings:** em um treino curto, a similaridade entre "gato" e "cachorro" sobe de 0,09 para 0,81.
- **Fine-tuning:** uma rede pré-treinada é especializada em uma tarefa nova com 40 exemplos. A acurácia no teste vai de 69,4% para 85,8%, com o efeito colateral de esquecer parte da tarefa original (de 99,3% para 79,0%).
- **LoRA:** mesma ideia com 260 parâmetros treináveis, contra 1.153 do ajuste completo.
- **Persistência:** os pesos são salvos, carregados em uma instância nova e produzem saídas idênticas. O checkpoint completo permite retomar um treino.
- **Inferência:** um modelo de linguagem de caracteres gera texto, e o gráfico mostra como a temperatura muda a distribuição de probabilidades.
- **Multimodalidade:** uma imagem vira uma sequência de vetores, um sinal de áudio vira espectrograma, e um mini-CLIP aprende a associar imagem e legenda.
- **Operação:** a quantização para `int8` reduz o modelo a cerca de um quarto do tamanho, praticamente sem alterar a perda de validação.

> Os valores acima vêm de execuções com semente fixa em modelos minúsculos. Eles ilustram os conceitos e não representam o desempenho de LLMs reais.

## 🛠️ Tecnologias

| Biblioteca | Uso no notebook |
|---|---|
| **Python 3** | Linguagem dos experimentos |
| **PyTorch** | Redes neurais, autograd, treinamento e persistência (`state_dict`) |
| **NumPy** | Cálculos numéricos e visualização dos conceitos |
| **Matplotlib** | Gráficos e mapas de calor |
| `transformers` (opcional) | Apenas uma célula que compara com um tokenizador real, desligada por padrão |

Além disso, são usados módulos da biblioteca padrão, como `math`, `re`, `os`, `tempfile`, `time`, `copy` e `collections`.

## 🚀 Como executar

**1. Instale as dependências**

```bash
pip install numpy torch matplotlib notebook
```

> O notebook foi executado em CPU, com Python 3.12, PyTorch 2.13, NumPy 2.5 e Matplotlib 3.11. O pacote `notebook` fornece o Jupyter; use outro ambiente de sua preferência, se quiser.

**2. Abra o notebook**

```bash
jupyter notebook RedeNeuralTransformer.ipynb
```

**3. Execute as células na ordem**

Use *Run All* ou execute célula por célula. Os capítulos são progressivos e alguns reutilizam modelos criados antes, então vale seguir a ordem apresentada.

**Opcional:** também é possível executar tudo pelo terminal.

```bash
python -m nbconvert --to notebook --execute RedeNeuralTransformer.ipynb --output executado.ipynb
```

Para ativar a comparação com um tokenizador real no capítulo 2, instale `transformers`, defina `USAR_HUGGINGFACE = True` na primeira célula de código e tenha acesso à internet. Esse passo não é necessário para o restante do notebook.

## 📁 Estrutura do repositório

```text
.
├── RedeNeuralTransformer.ipynb                  # Notebook principal (10 capítulos)
├── Modelos_de_Linguagem_em_Larga_Escala.ipynb   # Material de referência da FIAP
└── README.md
```

## 📚 Referências

- **FIAP**, *Modelos de Linguagem em Larga Escala*, material do Prof. Orlando Junior ([`Modelos_de_Linguagem_em_Larga_Escala.ipynb`](Modelos_de_Linguagem_em_Larga_Escala.ipynb)). Ele apresenta aplicações com a biblioteca `transformers`, como análise de sentimentos, classificação zero-shot, geração de texto, NER, Q&A, sumarização e tradução. Foi usado como referência para a organização entre teoria e prática. Esse material é separado do notebook principal, **requer `transformers`** e baixa modelos da Hugging Face.
- Vaswani et al., [*Attention Is All You Need*](https://arxiv.org/abs/1706.03762) (2017), artigo que introduziu o Transformer, citado no material da FIAP.
