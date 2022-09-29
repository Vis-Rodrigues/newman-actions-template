# Template de Actions para execução das coleções do Postman com Newman

Template de Github Actions para ser reutilizado nos projetos com Postman.
Este repositório possui templates para lint das coleções e environments do Postman, execução dos testes, publicação do resultado no Github Pages e adição de comentários automáticos nos PRs com resultado dos testes.

Lista de comandos que serão executados:

- checkout
- download a artifact
- json to variables
- add pr comment

## Inputs
| Nome | Descrição | Requirida |Default |
|------|-----------|-----------|--------|
|`pr_title` | Titulo do comentário no PR | não | Resultado da última execução |
|`artifact_name` | Nome do artefato para download | sim | report |
|`report_json_path`| Caminho do arquivo json. Incluir extensão. | sim | false |

## Como utilizar 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

#### Utilizando job unificado
#TODO

#### Utilizando jobs apartados

```yaml
name: "Executar Testes com Newman"
on:
  push:
    branches:
      - '*'
    paths:
      - '**.json'
  pull_request:

jobs:

  comment-pr-newman:
      uses: "Vis-Rodrigues/newman-actions-template/.github/workflows/pr-comment-newman.yaml@main"
      with:
        pr_title: "Resultado da última execução"
        artifact_name: "report"
        report_json_path: "report/result.json"
```