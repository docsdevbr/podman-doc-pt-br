..
  Copyright (c) 2026 Podman Container Tools, a Series of LF Projects, LLC.
  Podman Container Tools™ is a trademark of LF Projects, LLC.

  Documentation licensed under the Apache License, Version 2.0.
  The original work was translated from English into Brazilian Portuguese.
  https://github.com/containers/podman/blob/-/LICENSE

  source_url: https://github.com/containers/podman/blob/v5.8/docs/source/Commands.rst
  revision: f293c1a179d905d264026e24973a00da98ea1a82
  status: ready

.. include:: includes.rst

Comandos
========

:doc:`Podman <markdown/podman.1>` (Pod Manager) Opções globais, variáveis de
ambiente, códigos de saída, arquivos de configuração e mais.

:doc:`artifact <markdown/podman-artifact.1>` Gerencia artefatos OCI.

:doc:`attach <markdown/podman-attach.1>` Anexa a um contêiner em execução.

:doc:`auto-update <markdown/podman-auto-update.1>` Atualiza automaticamente os
contêineres de acordo com sua política de atualização automática.

:doc:`build <markdown/podman-build.1>` Cria uma imagem usando as instruções do
Containerfile.

:doc:`commit <markdown/podman-commit.1>` Cria uma nova imagem com base no
contêiner alterado.

:doc:`container <markdown/podman-container.1>` Gerencia contêineres.

:doc:`cp <markdown/podman-cp.1>` Copia arquivos/pastas entre um contêiner e o
sistema de arquivos local.

:doc:`create <markdown/podman-create.1>` Cria um contêiner, mas não o inicie.

:doc:`diff <markdown/podman-diff.1>` Exibe as alterações no sistema de arquivos
do objeto.

:doc:`events <markdown/podman-events.1>` Exibe os eventos do sistema do Podman.

:doc:`exec <markdown/podman-exec.1>` Executa um processo em um contêiner em
execução.

:doc:`export <markdown/podman-export.1>` Exporta o conteúdo do sistema de
arquivos do contêiner como um arquivo tar.

:doc:`farm <markdown/podman-farm.1>` Distribui construções para máquinas
remotas.

:doc:`generate <markdown/podman-generate.1>` Gera dados estruturados com base em
contêineres, pods ou volumes.

:doc:`healthcheck <markdown/podman-healthcheck.1>` Gerencia verificações de
integridade em contêineres.

:doc:`history <markdown/podman-history.1>` Exibe o histórico de uma imagem
específica.

:doc:`image <markdown/podman-image.1>` Gerencia imagens.

:doc:`images <markdown/podman-images.1>` Lista imagens no armazenamento local.

:doc:`import <markdown/podman-import.1>` Importa um arquivo tar para criar uma
imagem do sistema de arquivos.

:doc:`info <markdown/podman-info.1>` Exibe informações do sistema do Podman.

:doc:`init <markdown/podman-init.1>` Inicializa um ou mais contêineres.

:doc:`inspect <markdown/podman-inspect.1>` Exibe a configuração do objeto
indicado pelo ID.

:doc:`kill <markdown/podman-kill.1>` Encerra um ou mais contêineres em execução
com um sinal específico.

:doc:`kube <markdown/podman-kube.1>` Executa contêineres, pods ou volumes a
partir de um arquivo estruturado.

:doc:`load <markdown/podman-load.1>` Carregar imagens de um arquivo tar.

:doc:`login <markdown/podman-login.1>` Faz o login em um registro de
contêineres.

:doc:`logout <markdown/podman-logout.1>` Faz o logout de um registro de
contêineres.

:doc:`logs <markdown/podman-logs.1>` Obtém os logs de um ou mais contêineres.

:doc:`machine <markdown/podman-machine.1>` Gerencia uma máquina virtual.

:doc:`manifest <markdown/podman-manifest.1>` Manipula listas de manifestos e
índices de imagens.

:doc:`mount <markdown/podman-mount.1>` Monta o sistema de arquivos raiz de um
contêiner em execução.

:doc:`network <markdown/podman-network.1>` Gerencia redes.

:doc:`pause <markdown/podman-pause.1>` Pausa todos os processos em um ou mais
contêineres.

:doc:`pod <markdown/podman-pod.1>` Gerencia pods.

:doc:`port <markdown/podman-port.1>` Lista os mapeamentos de portas ou um
mapeamento específico do contêiner.

:doc:`ps <markdown/podman-ps.1>` Lista contêineres.

:doc:`pull <markdown/podman-pull.1>` Baixa uma imagem de um registro.

:doc:`push <markdown/podman-push.1>` Envia uma imagem para um destino
especificado.

:doc:`quadlet <markdown/podman-quadlet.1>` Permite que as pessoas usuárias
gerenciem Quadlets.

:doc:`rename <markdown/podman-rename.1>` Renomeia um contêiner existente.

:doc:`restart <markdown/podman-restart.1>` Reinicia um ou mais contêineres.

:doc:`rm <markdown/podman-rm.1>` Remove um ou mais contêineres.

:doc:`rmi <markdown/podman-rmi.1>` Remove uma ou mais imagens do armazenamento
local.

:doc:`run <markdown/podman-run.1>` Executa um comando em um novo contêiner.

:doc:`save <markdown/podman-save.1>` Salva imagens em um arquivo.

:doc:`search <markdown/podman-search.1>` Busca imagens no registro.

:doc:`secret <markdown/podman-secret.1>` Gerencia segredos.

:doc:`start <markdown/podman-start.1>` Inicia um ou mais contêineres.

:doc:`stats <markdown/podman-stats.1>` Exibe um fluxo contínuo de estatísticas
de uso de recursos do contêiner.

:doc:`stop <markdown/podman-stop.1>` Interrompe um ou mais contêineres.

:doc:`system <markdown/podman-system.1>` Gerencia o Podman.

:doc:`tag <markdown/podman-tag.1>` Adiciona um nome adicional a uma imagem
local.

:doc:`top <markdown/podman-top.1>` Exibe os processos em execução em um
contêiner.

:doc:`unmount <markdown/podman-unmount.1>` Desmonta o sistema de arquivos raiz
de um contêiner em execução.

:doc:`unpause <markdown/podman-unpause.1>` Retoma a execução dos processos em um
ou mais contêineres.

:doc:`unshare <markdown/podman-unshare.1>` Executa um comando em um namespace de
usuário modificado.

:doc:`untag <markdown/podman-untag.1>` Remove um nome de uma imagem local.

:doc:`update <markdown/podman-update.1>` Atualiza um contêiner existente.

:doc:`version <markdown/podman-version.1>` Exibe informações da versão do
Podman.

:doc:`volume <markdown/podman-volume.1>` Gerencia volumes.

:doc:`wait <markdown/podman-wait.1>` Bloqueia um ou mais contêineres.
