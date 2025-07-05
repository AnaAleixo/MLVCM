# 🧠 Modelo Preditivo de Violência Contra a Mulher em Pernambuco

**Autora:** Ana Cláudia de Lima Aleixo  
**Instituição:** Universidade Federal de Pernambuco (UFPE)  
**Ano:** 2025  

Este notebook faz parte da dissertação de mestrado da autora, com o objetivo de desenvolver um modelo preditivo utilizando o algoritmo Random Forest para auxiliar na gestão de políticas públicas voltadas ao enfrentamento da violência contra a mulher em Pernambuco.

**Licença:** Este código está licenciado sob a [MIT License](../LICENSE).
Você pode:
- Compartilhar — copiar e redistribuir os dados em qualquer formato
- Adaptar — remixar, transformar e criar a partir dos dados

Desde que atribua o devido crédito à autora (Ana Cláudia de Lima Aleixo) e à fonte original dos dados, quando aplicável.

# Aprendizado de Máquina Dissertação
Modelo preditivo de violência contra a mulher em Pernambuco usando Random Forest, com foco em apoiar políticas públicas.
# Dados utilizados no projeto

Este diretório contém os dados utilizados na dissertação de mestrado de Ana Cláudia de Lima Aleixo (UFPE), cujo objetivo é desenvolver um modelo preditivo de violência contra a mulher em Pernambuco.

## 📌 Origem dos dados
# Dados utilizados no projeto

Este diretório contém três arquivos em formato `.xlsx` com os dados de registros de violência contra a mulher em Pernambuco:

## 📂 Arquivos disponíveis

- `dados_2015_2025.xlsx`: base completa com dados de janeiro de 2015 a janeiro de 2025.
- `dados_2015_2019.xlsx`: recorte correspondente ao primeiro período de análise (5 anos).
- `dados_2020_2024.xlsx`: recorte correspondente ao segundo período de análise (5 anos).

## 🗒️ Observações

- Os arquivos contêm dados anonimizados, agregados por período, município e características da ocorrência.
- Os dados foram utilizados para fins acadêmicos no contexto da dissertação de mestrado.
- Fontes: [especifique a(s) fonte(s) oficial(is) se possível – ex: SINESP, IBGE, Secretaria da Mulher etc.]

## 📜 Licença

Licenciados sob [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), permitindo o uso, redistribuição e adaptação com atribuição adequada à autora Ana Cláudia de Lima Aleixo e às fontes originais.

Os dados foram obtidos de fontes públicas, como sistemas de estatísticas de segurança pública, portais governamentais e bases abertos, sem identificação pessoal ou sensível.

## 📜 Licença dos dados

Os dados estão disponibilizados sob a licença [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

> **Nota:** Se houver dados sensíveis, confidenciais ou restritos, eles **não estão incluídos** neste repositório.
>
> ## 📊 Acesso estruturado aos dados no notebook

Este projeto utiliza três arquivos de dados:

- `dados_2015_2019.csv` → hospedado no GitHub
- `dados_2020_2024.csv` → hospedado no GitHub
- `dados_geral_sem_jan2025.csv` → armazenado no Google Drive (uso pessoal)

### ✅ Bloco de código inicial (para usar no Colab)

```python
import pandas as pd
from google.colab import drive

# URLs públicas do GitHub
URL_DADOS_2015_2019 = "https://raw.githubusercontent.com/AnaAleixo/MLVCM/main/dados_2015_2019.csv"
URL_DADOS_2020_2024 = "https://raw.githubusercontent.com/AnaAleixo/MLVCM/main/dados_2020_2024.csv"

# Montar o Google Drive
drive.mount('/content/drive', force_remount=True)

# Caminho local no Drive
CAMINHO_DADOS_GERAL = "/content/drive/MyDrive/dados_geral_sem_jan2025.csv"

# Função para carregar sob demanda
def carregar_dados(origem, tipo='url'):
    """
    Carrega um DataFrame de URL (GitHub) ou caminho local (Drive).
    """
    try:
        if tipo == 'url':
            df = pd.read_csv(origem)
            print(f"✅ Dados carregados da URL: {origem.split('/')[-1]}")
        elif tipo == 'local':
            df = pd.read_csv(origem)
            print(f"✅ Dados carregados do Drive: {origem}")
        else:
            print("❌ Tipo de origem inválido. Use 'url' ou 'local'.")
            return None
        return df
    except Exception as e:
        print("❌ Erro ao carregar os dados:", e)
        return None

# Carregar dados de 2015 a 2019 (GitHub)
df_2015 = carregar_dados(URL_DADOS_2015_2019, tipo='url')

# Carregar dados de 2020 a 2024 (GitHub)
df_2020 = carregar_dados(URL_DADOS_2020_2024, tipo='url')

# Carregar dados gerais (Google Drive)
df_geral = carregar_dados(CAMINHO_DADOS_GERAL, tipo='local')

