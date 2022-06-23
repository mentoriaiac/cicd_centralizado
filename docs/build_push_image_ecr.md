# Faz o build, tag e push da imagem para repositório AWS ECR
Faz o build, tag e push da imagem docker para AWS ECR. 
- O usuário pode passar uma tag para imagem de forma estática para isso utilize o input TAG_IMAGE.
- Se o usuário não definir um valor para input TAG_IMAGE o workflow irá utilizar os 8 caracteres do hash do commit.

## Inputs
| Nome | Descrição | Requirida |Default |
|------|-----------|-----------|--------|
|`OS_VERSION` | Versão do sistema operacional | não | ubuntu-20.04 |
|`TAG_IMAGE` | Tag da imagem docker | não | 8 dígitos do hash do commit  |
|`WORK_DIR` | Diretório do projeto | não | . |
|`ECR_REPOSITORY` | Nome do repositório AWS ECR | sim | n/a |
|`AWS_REGION` | Região da AWS | sim | n/a |
|`DOCKERFILE` | Path do arquivo dockerfile | não | ./Dockerfile |

## Secret
| Nome | Descrição | Requirida |Default |
|------|-----------|-----------|--------|
|`AWS_ACCESS_KEY_ID` | ID de acesso do usuário IAM | sim | n/a |
|`AWS_SECRET_ACCESS_KEY` | Segredo de acesso do usuário IAM | sim | n/a |


## Utilizando 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

```yaml
name: Build, Tag e Push da imagem para repositório ECR
on:
  push:
    branches:
      - "main"
  workflow_dispatch:

jobs:
  build_tag_push:
    uses: "mentoriaiac/cicd_centralizado/.github/workflows/build_push_image_ecr.yaml@v1"
    with:
      ECR_REPOSITORY: "NOME-REPOSITORIO"
    secrets:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```
