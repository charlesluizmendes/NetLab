# Proposições

Análise de proposições da Câmara dos Deputados sobre impactos ambientais da inteligência artificial e da infraestrutura digital, entre 2023 e 2025.

## Metodologia

A pesquisa usa a API de Dados Abertos da Câmara para coletar ementas de projetos de lei (PL), projetos de lei complementar (PLP), propostas de emenda à Constituição (PEC) e medidas provisórias (MPV) apresentadas entre 2023 e 2025.

Na etapa de limpeza, o notebook remove registros sem ID, tipo, data ou ementa e elimina proposições duplicadas. Em seguida, seleciona ementas que contêm ao menos um termo relacionado à tecnologia e um termo relacionado ao meio ambiente.

O TF-IDF transforma as ementas selecionadas em números e destaca os termos mais relevantes do conjunto. O GPT participa da análise classificando cada proposição como relação ambiental direta, indireta, ausente ou incerta, indicando os temas, resumindo a abordagem e copiando uma evidência literal da ementa.

A validação registra a quantidade de dados coletados, dados incompletos, duplicatas, proposições limpas e candidatos selecionados. Depois da classificação, o notebook verifica se a evidência informada pelo GPT aparece na ementa. A análise é exploratória, pois depende das palavras-chave e de textos resumidos; ela não mede impactos ambientais reais nem substitui a leitura do inteiro teor.

## Instalação

Ative a venv e instale as dependências:

```bash
source venv/bin/activate
python -m pip install -r requirements.txt
```

No Windows, ative a venv com `venv\Scripts\activate`.

## Configuração da OpenAI

Crie um arquivo `.env` na pasta principal do projeto com:

```env
OPENAI_API_KEY=sua-chave-da-api
OPENAI_MODEL=gpt-4.1-mini
```

O notebook pede a chave durante a execução se ela não estiver no `.env`. Não compartilhe nem publique sua chave. O `.env` está no `.gitignore`.

## Execução

Abra `src/proposicoes.ipynb` no Jupyter, VS Code ou Google Colab e execute as células em ordem, do início ao fim.

## Etapas

- `01_coleta`: consulta as proposições na API da Câmara e salva `proposicoes_brutas.csv`.
- `02_limpeza`: remove registros incompletos e duplicados e salva `candidatos_gpt.csv`.
- `03_classificacao`: classifica as ementas com o modelo OpenAI e salva `classificacoes_gpt.csv`.
- `04_revisao`: confere as classificações e salva `revisao_resultados.csv`.
- `05_visualizacao`: cria os gráficos e salva os termos TF-IDF.

Os arquivos são salvos dentro da pasta `outputs`.

## Resposta da pesquisa

Entre as cinco proposições selecionadas, duas tratam diretamente de impactos ambientais da infraestrutura digital, duas relacionam tecnologia e proteção ambiental de forma indireta e uma menciona IA sem relação ambiental. O debate encontrado se concentra em eficiência energética, sustentabilidade e licenciamento de data centers; o consumo de água não aparece como tema direto nas ementas analisadas. Essa conclusão é exploratória e se aplica ao conjunto selecionado por palavras-chave.
