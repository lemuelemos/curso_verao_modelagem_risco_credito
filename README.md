# Introdução ao Credit Scoring

[![GitHub Pages](https://github.com/lemuelemos/curso_verao_modelagem_risco_credito/actions/workflows/pages.yml/badge.svg)](https://github.com/lemuelemos/curso_verao_modelagem_risco_credito/actions/workflows/pages.yml)

Site do curso **Introdução ao Credit Scoring**, oferecido no Programa de Verão do IME-USP.

O curso apresenta os fundamentos conceituais e práticos do credit scoring: da definição do problema e preparação dos dados até a estimação por regressão logística, construção do scorecard, avaliação de desempenho, implantação e monitoramento — com demonstrações em Python.

- **Carga horária:** 15 horas (5 aulas síncronas de 3 horas, online)
- **Site:** <https://lemuelemos.github.io/curso_verao_modelagem_risco_credito/>
- **Referência principal:** SICSÚ, A. L. *Credit scoring: desenvolvimento, implantação e acompanhamento com Python*. 2. ed. Blucher, 2026.

## Ambiente Python com uv

O ambiente do curso é gerenciado com [uv](https://docs.astral.sh/uv/). Não é necessário instalar Python separadamente: o `uv` instala a versão definida em `.python-version` e cria um ambiente isolado em `.venv`.

Depois de [instalar o uv](https://docs.astral.sh/uv/getting-started/installation/), execute na raiz do projeto:

```bash
uv python install
uv venv
uv pip sync requirements.txt
```

Para trabalhar com os notebooks, abra esta pasta no [VS Code](https://code.visualstudio.com/) ou no [Positron](https://positron.posit.co/) e selecione o interpretador Python existente em `.venv`.

Também é possível iniciar o JupyterLab pelo terminal. Ative primeiro o ambiente:

```powershell
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
jupyter lab
```

```bash
# macOS ou Linux
source .venv/bin/activate
jupyter lab
```

## Desenvolvimento do site

Além do ambiente Python, instale o [Quarto](https://quarto.org/docs/get-started/). Para visualizar o site durante a edição:

```bash
quarto preview
```

Para gerar a versão estática em `_site/`:

```bash
quarto render
```

O diretório `_site/` é um artefato de build e não é versionado.

### Atualização das dependências

As dependências diretas ficam em `requirements.in`. Após alterá-las, gere novamente o arquivo congelado e sincronize o ambiente:

```bash
uv pip compile requirements.in --universal --python-version 3.13 --output-file requirements.txt
uv pip sync requirements.txt
```

Não edite `requirements.txt` manualmente.

## Publicação no GitHub Pages

O workflow `.github/workflows/pages.yml` executa duas rotinas:

1. em todo pull request, instala o ambiente com `uv` e valida a renderização completa do site;
2. em todo push para `main`, repete a validação e publica `_site/` no GitHub Pages.

No repositório do GitHub, a fonte de publicação deve estar configurada como **GitHub Actions** em **Settings > Pages**. A primeira execução bem-sucedida do workflow cria o ambiente `github-pages` e disponibiliza o endereço do site.

## Licença

Conteúdo sob licença [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.pt-br).
