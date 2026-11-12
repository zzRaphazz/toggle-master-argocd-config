# Configuração do Argo CD — ToggleMaster

Este repositório contém a Application raiz e as Applications filhas para os cinco workloads de serviço. A Application raiz lê `applications/` deste repositório; cada filha lê o diretório Kustomize do serviço em `toggle-master-k8s-manifests`.

Os repositórios são públicos, então o Argo CD pode lê-los sem credenciais Git. Se a visibilidade mudar, configure uma credencial somente-leitura no namespace `argocd`; nunca faça commit de credenciais aqui.

## Bootstrap

Após instalar o Argo CD no cluster EKS existente e validar o acesso à conta AWS/cluster, um operador autorizado aplica `root-application.yaml` uma vez. A Application raiz cria as Applications filhas. Não execute esse bootstrap pelo CI dos serviços.

As referências iniciais de imagem nos manifests são placeholders até configurar a conta AWS alvo e os repositórios ECR.
