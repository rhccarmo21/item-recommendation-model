# 📦 Item Recommendation Model

> Sistema simples de recomendação baseado em filtragem colaborativa, ideal para fins didáticos.

---

## 📌 Objetivo

Implementar um sistema de recomendação de produtos utilizando similaridade entre usuários ou itens. A proposta simula, em pequena escala, o funcionamento de plataformas como Amazon e Netflix, com foco educativo.

---

## 🛠 Tecnologias

- **Python 3.10+**
- **Pandas**, **NumPy**
- **Scikit-learn** – Cálculo de similaridade
- **Matplotlib / Seaborn** – Visualização (opcional)
- **Jupyter Notebook** – Apresentação interativa dos resultados

---

## 📊 Funcionalidades

- Geração da matriz usuário × item  
- Cálculo de similaridade (coseno)  
- Recomendações personalizadas por perfil de usuário  
- Visualização dos itens recomendados

---

## 🚀 Execução

```bash
# Clone o repositório
git clone git@github.com:rhccarmo21/item-recommendation-model.git
cd item-recommendation-model

# (Opcional) Crie e ative um ambiente virtual
python -m venv venv
source venv/bin/activate       # Linux/macOS
venv\Scripts\activate          # Windows

# Instale as dependências
pip install -r requirements.txt

# Execute o notebook principal
jupyter notebook recommendation_model.ipynb

📁 Estrutura

item-recommendation-model/
├── data/           # Dados fictícios de usuários e itens
├── notebook/       # Notebook com a lógica do sistema
├── src/            # Código-fonte modularizado
├── README.md       # Documentação do projeto
└── requirements.txt

🧪 Exemplo de Uso
Entrada:
Usuário X avaliou:

Produto A: ⭐⭐⭐⭐

Produto B: ⭐⭐⭐⭐⭐

Saída:
Recomendação do Produto C com base em usuários similares que avaliaram A e B.

🔍 Expansões Futuras
- Adição de modelo híbrido (conteúdo + colaborativo)
- Avaliação com métricas como Precision@k e Recall@k
- Interface com Streamlit ou Gradio
- Deploy via API com ferramentas de MLOps

📄 Licença
Distribuído sob a Licença MIT.


