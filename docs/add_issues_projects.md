# Ansible Valida Role
Use esta actions para adicionar automaticamente as issues a um projeto do GitHub. Observe que isso é para projetos do GitHub (beta), não para os projetos originais do GitHub.

## Inputs
| Nome | Descrição | Requirida |Default |
|------|-----------|-----------|--------|
|`project_url` | URL do projeto beta do Github | sim | n/d |
|`github_token` | Personal token para leitura/escrita no projeto Github | sim | s/n |


## Utilizando 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

```yaml
name: "Adiciona Issues em Projects GitHub"
  
on:
  issues:
    types:
      - opened
jobs:
  add-issue:
    uses: "mentoriaiac/cicd_centralizado/.github/workflows/add-issues-projects.yaml@v1"
    secrets:
      github_token: ${{ secrets.ADD_TO_PROJECT_PAT }}
```
