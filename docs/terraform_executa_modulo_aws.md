# Terraform Executa Modulo
Github Actions para ser reutilizado nos projetos que utilizam Terraform, com a finalidade de criar uma infra baseada em um modulo.

## Inputs
| Nome | Descrição | Requirida | Default |
|------|-----------|-----------|---------|
| `aws_region` | Região AWS | sim | N/A |
| `os_version` | Versão do sistema operacional | não | ubuntu-20.04 |
| `tf_workspace` | Seleciona o Workspace | não | default |

## Secrets

| Nome | Descrição | Requerida | Default |
|------|-----------|-----------|---------|
| `AWS_ACCESS_KEY_ID` | Credencial AWS | Sim | N/A |
| `AWS_SECRET_ACCESS_KEY` | Credencial AWS | Sim | N/A |

## Utilizando 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

```yaml
name: "Terraform Executa Modulo"

on:
  push:
    branches:
      - main
  
jobs:
  terraform:
    uses: "mentoriaiac/cicd_centralizado/.github/workflows/terraform_executa_modulo_aws.yaml@v1"
    with:
      aws_region: "us-east-1"
      tf_workspace: "default"
    secrets:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```
