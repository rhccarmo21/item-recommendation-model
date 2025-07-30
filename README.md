
# 🧠 Item Recommendation Model

[![Licença MIT](https://img.shields.io/badge/Licença-MIT-green)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/downloads/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.0%2B-orange)](https://scikit-learn.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.6%2B-FF6F00)](https://www.tensorflow.org/)

## 📌 Sumário
1. [Visão Geral](#-visão-geral)  
2. [Modelos Implementados](#-modelos-implementados)
3. [Pipeline de Dados](#-pipeline-de-dados)
4. [Métricas de Avaliação](#-métricas-de-avaliação)
5. [Instalação](#-instalação)
6. [Como Usar](#-como-usar)
7. [Exemplos](#-exemplos)
8. [Contribuição](#-contribuição)
9. [Licença](#-licença)

---

## 🌐 Visão Geral

Sistema de recomendação baseado em múltiplas abordagens:

- **Similaridade de conteúdo** (cosine similarity)
- **Filtragem colaborativa** (KNN, matrix factorization)
- **Modelos híbridos** (combina conteúdo + comportamento)
- **Deep Learning** (autoencoders, GNN)

**Aplicações:**
- E-commerce (produtos similares)
- Streaming (conteúdo personalizado)
- Sistemas de informação (artigos relacionados)
- Plataformas educacionais

---

## 🧮 Modelos Implementados

### 1. Baseados em Similaridade
| Modelo | Descrição | Hiperparâmetros |
|--------|-----------|-----------------|
| Cosine Similarity | Distância angular entre vetores | `metric='cosine'` |
| Jaccard Index | Similaridade de conjuntos | `binary=True` |

### 2. Filtragem Colaborativa
| Modelo | Descrição | Vantagens |
|--------|-----------|-----------|
| KNN | K-vizinhos mais próximos | Simplicidade |
| ALS | Fatoração de matriz implícita | Escalabilidade |

### 3. Modelos Híbridos
```python
class HybridRecommender:
    def __init__(self, content_weight=0.3, cf_weight=0.7):
        self.content_model = ContentBased()
        self.cf_model = CollaborativeFiltering()
```

---

## 📂 Pipeline de Dados

### Pré-processamento
```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer(stop_words='english')
item_features = tfidf.fit_transform(item_descriptions)
```

### Matriz de Interações
| UserID | ItemID | Rating | Timestamp |
|--------|--------|--------|-----------|
| 1 | 101 | 5 | 1636547890 |
| 1 | 205 | 3 | 1636547990 |

```python
interaction_matrix = pd.pivot_table(
    data=ratings_df,
    values='rating',
    index='user_id',
    columns='item_id',
    fill_value=0
)
```

---

## 📊 Métricas de Avaliação

| Métrica | Fórmula | Interpretação |
|---------|---------|---------------|
| Precision@K | `TP@K / K` | Relevância dos top K |
| Recall@K | `TP@K / Total Relevant` | Cobertura de itens relevantes |
| MAP | `Mean Average Precision` | Ordem das recomendações |
| NDCG | `Discounted Cumulative Gain` | Posicionamento relativo |

```python
from evaluation import calculate_metrics

metrics = calculate_metrics(
    true_items=test_set,
    recommended_items=predictions,
    k=10
)
```

---

## ⚙️ Instalação

### Via pip
```bash
pip install recsys-toolkit
```

### Ambiente Conda
```bash
conda create -n recsys python=3.9
conda activate recsys
pip install -r requirements.txt
```

### Docker
```bash
docker pull recsys/engine:latest
```

---

## 🚀 Como Usar

### 1. Treinamento Básico
```python
from recsys.models import KNNRecommender

model = KNNRecommender(
    n_neighbors=50,
    metric='cosine'
)
model.fit(interaction_matrix)
```

### 2. Recomendação em Batch
```python
recommendations = model.batch_predict(
    user_ids=test_users,
    n_recommendations=10
)
```

### 3. API REST
```python
from recsys.api import RecommendationAPI

api = RecommendationAPI(model)
api.run(port=8000)
```

---

## 🛒 Exemplos Práticos

### Caso 1: E-commerce
```python
from recsys.utils import load_product_data

data = load_product_data('ecommerce')
model = HybridRecommender()
model.fit(data)
print(model.recommend(user_id=123))
```

### Caso 2: Sistema de Notícias
```python
news_model = ContentBasedRecommender(
    vectorizer='tfidf',
    ngrams=(1, 3)
news_model.train(articles_df)
```

---

## 🗂 Estrutura do Projeto

```
recsys-toolkit/
├── data/
│   ├── sample/          # Datasets de exemplo
├── recsys/
│   ├── models/          # Implementações dos modelos
│   ├── evaluation/      # Métricas de avaliação
│   ├── utils/           # Funções auxiliares
├── notebooks/
│   ├── benchmarks.ipynb # Comparação de modelos
└── tests/
```

---

## 🤝 Contribuição

1. **Adicionar Modelos**:
   ```python
   class NewModel(BaseRecommender):
       def __init__(self, param1=0.5):
           self.param1 = param1
       
       def fit(self, data):
           # Implementação aqui
   ```

2. **Padrões de Código**:
   ```python
   def cosine_similarity(A, B):
       """Calcula similaridade cosseno entre duas matrizes
       
       Args:
           A: Matriz de features (n_samples, n_features)
           B: Matriz de features (m_samples, n_features)
           
       Returns:
           Matriz de similaridade (n_samples, m_samples)
       """
       return dot_product / (norm_A * norm_B)
   ```

3. **Testes**:
   ```bash
   pytest tests/test_models.py -v
   ```

---

## 📜 Licença

```text
MIT License

Copyright (c) 2023 Recommender Systems Toolkit

Permissão é concedida...
```

---

💡 **Para Implementação em Produção:**
- Adicionar cache para recomendações frequentes
- Implementar mecanismos de fallback
- Monitorar drift de dados continuamente

[📘 Documentação Completa](https://recsys-toolkit.readthedocs.io) | [🎮 Playground Interativo](https://colab.research.google.com/recsys-demo)
```

### Destaques Específicos:

1. **Escalonamento**: Suporte a matrizes esparsas (SciPy)
2. **Cold Start**: Estratégias para novos itens/usuários
3. **Explicabilidade**: Geração de razões para recomendações
4. **Deploy**: Modelos exportáveis como ONNX
5. **Benchmarking**: Comparação automática de abordagens

### Para Implementação:

1. Definir schema de dados de interação
2. Escolher modelo baseado no caso de uso
3. Configurar pipeline de treinamento contínuo
4. Implementar sistema de feedback implícito
5. Monitorar métricas de negócio (CTR, conversão)