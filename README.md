# 🦟 Predição de Níveis de Alerta de Dengue com Machine Learning
> **Estudo de Caso:** Transpondo barreiras geográficas através de Inteligência Epidemiológica com dados de 2025.

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn">
</p>

## 📋 Resumo do Projeto
Este projeto utiliza Machine Learning para prever o nível de alerta epidemiológico da Dengue (1 a 4). O diferencial técnico reside na superação do **Domain Shift**: o modelo foi treinado com dados de **Uberlândia-MG** e validado com sucesso na metrópole de **São Paulo-SP**, utilizando o histórico completo do ano de **2025**.

## 📂 Fonte dos Dados
Os dados brutos foram extraídos via **InfoDengue (Fiocruz/FGV)**, abrangendo:
* **Recorte Temporal:** Janeiro de 2025 a Dezembro de 2025.
* **Cidades:** Uberlândia (MG) e São Paulo (SP).
* **Variáveis:** Dados climáticos (temperatura, umidade) e índices de receptividade ambiental.

---

## 🔬 Metodologia: Do Local ao Universal

Durante o desenvolvimento, identificamos que variáveis absolutas de incidência hospitalar causavam *overfitting* geográfico. Para resolver isso, pivotamos para um modelo **Agnóstico de Região**.

---

## 📊 Análise de Performance e Gráficos (2025)

### 1. Performance em Uberlândia (Treino/Teste)
Base de controle onde o modelo aprendeu as assinaturas biológicas da Dengue.

**[COLOQUE AQUI O SEU PRINT: image_a21371.png]**

* **Random Forest:** 79% de Acurácia.
* **Contexto:** Treinado com o histórico climático de 2025 da cidade.

### 2. Validação Externa (São Paulo)
O teste definitivo de escalonabilidade em uma realidade urbana distinta.

**[COLOQUE AQUI O SEU PRINT: image_a2961c.png]**

* **Random Forest:** 68% de Acurácia.
* **Análise:** O modelo provou que os padrões climáticos de 2025 em SP seguem a mesma lógica biológica aprendida em Uberlândia.

---

## ⚙️ Engenharia de Recursos (Features)
Para garantir a estabilidade preditiva em diferentes cidades, o modelo utiliza:
* **`tempmed`**: Temperatura média (Impacto direto no ciclo do mosquito).
* **`umidmed`**: Umidade média (Essencial para a eclosão de ovos).
* **`receptivo`**: Fator de receptividade biológica.
* **`Mes`**: Variável de sazonalidade extraída das datas de 2025.

---

## 🚀 Como utilizar o modelo
O modelo foi exportado via `joblib`. Você pode carregar o pipeline e aplicar em qualquer cidade que possua dados climáticos compatíveis:

```python
import joblib

# Carregar modelo treinado com dados de 2025
modelo = joblib.load('modelo_dengue_rf_clima.pkl')

# Exemplo de predição
previsao = modelo.predict(dados_climaticos_novos)
