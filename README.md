# Proposições

Análise de proposições da Câmara dos Deputados sobre impactos ambientais da inteligência artificial e da infraestrutura digital, entre 2023 e 2025.

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

O notebook também pede a chave durante a execução se ela não estiver no `.env`. Não compartilhe nem publique sua chave. O `.env` está no `.gitignore`.

## Execução

Abra `src/proposicoes.ipynb` no Jupyter ou VS Code e execute as células em ordem, do início ao fim. A primeira célula de código instala as bibliotecas usadas no notebook.

## Etapas

- `01_coleta`: consulta as proposições na API da Câmara e salva os dados recebidos.
- `02_limpeza`: remove registros incompletos e duplicados e seleciona ementas com termos de tecnologia e meio ambiente.
- `03_classificacao`: usa o modelo OpenAI configurado para classificar as ementas e registrar evidências.
- `04_revisao`: apresenta a tabela e o gráfico de resultados e salva `outputs/04_revisao/revisao_resultados.csv`.
