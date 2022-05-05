# Ansible Valida Role
Github Actions para ser reutilizado nos projetos de Ansible. Faz a validação da sintaxe da role Ansible. 

## Inputs
| Nome | Descrição | Requirida |Default |
|------|-----------|-----------|--------|
|`python_version` | Versão do python | não | 3.9 |
|`os_version` | Versão do sistema operacional | não | ubuntu-20.04 |


## Utilizando 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

```yaml
name: "Valida role ansible"
  
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  my_first_job:
    uses: "mentoriaiac/cicd_centralizado/.github/workflows/ansible_valida_role.yaml@v1"
    secrets:
      token: ${{ secrets.TOKEN }}
```
