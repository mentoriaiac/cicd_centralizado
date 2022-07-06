# Build, Lint, Scan e Push de imagem Docker
Github Actions para ser reutilizado nos projetos de Imagem Docker. Faz a processo de build, lint, scan e push da imagem. 


## Inputs
| Nome | Descrição | Requirida |Default | Type |
|------|-----------|-----------|--------|------|
| tag | tag da imagem docker | sim | N/A | string |
| os_version | Versão do sistema operacional | não | ubuntu-20.04 | string |
| hadolint_version | versão do hadolint | não | v2.9.2 | string |
| trivy_ignore | arquivo .trivyignore | não | "" | string |
| trivy_severity | nível de severidade para scan | não | "CRITICAL,HIGH" | string |
| push_image | escolha se deve ser feito push da imagem | não | não | boolean |


## Utilizando 
Criar a seguintes estrutura de diretórios: 

`.github/workflows/<proposito>.yml`

Utilize o exemplo abaixo para seu pipeline de CI:

```yaml
name: "Pipeline para build de imagem docker"
on:
  push:
  release:
    types: [created]
jobs:
  docker:
    uses: "mentoriaiac/cicd_centralizado/.github/workflows/docker_build.yaml@v1"
    with:
      tag: USUARIO/REPOSITORIO_DOCKER:TAG
      push_image: ${{github.event_name == 'release'}}
    secrets:
      docker_user: ${{secrets.DOCKER_LOGIN}}
      docker_password: ${{secrets.TOKEN_DOCKERHUB}}
```
