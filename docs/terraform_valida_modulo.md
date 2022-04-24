# Terraform Valida Módulo
Github Actions para ser reutilizado nos projetos de Terraform. Faz a validação da sintaxe do código terraform. 

- terraform init
- terraform fmt
- terraform validate
- validação tfsec

## Inputs
| Nome | Descrição | Requirida |Default |
|------|-----------|-----------|--------|
|`tf_version` | Versão do terraform | não | 1.0.0 |
|`os_version` | Versão do sistema operacional | não | ubuntu-20.04 |


## Utilizando 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

```yaml
name: "Terraform Valida Modulo"

on:
  push:
    - main
  pull_request:

jobs:
  terraform:
      uses: "mentoriaiac/cicd_centralizado/.github/workflows/terraform_valida_modulo.yaml@v1"
      with: 
        tf_version: "1.0.0"
        os_version: "ubuntu-20.04"
      secrets:
        token: ${{ secrets.TOKEN }}
```
