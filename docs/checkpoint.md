---
# Copyright (c) 2026 Podman Container Tools, a Series of LF Projects, LLC.
# Podman Container Tools™ is a trademark of LF Projects, LLC.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/containers/podman/blob/-/LICENSE

source_url: https://github.com/containers/podman.io/blob/main/docs/checkpoint.md
revision: 8d873f886942055b791c64678568b0cf2d6f0ec9
status: ready

title: Ponto de verificação do Podman
---

# Pontos de verificação

Os pontos de verificação funcionam atualmente apenas com contêineres com
privilégios de root.
Portanto, você precisa executar o contêiner de exemplo como root.
Em vez de prefixar cada comando com `sudo`, você também pode alternar para o
usuário root previamente usando `sudo -i`.

```bash
sudo podman run -d -p 8080:80/tcp docker.io/library/httpd
sudo podman ps
```

## Criando um ponto de verificação de um contêiner

Criar um ponto de verificação de um contêiner interrompe o contêiner enquanto
grava o estado de todos os processos no contêiner em disco.
Com isso, um contêiner pode ser restaurado posteriormente e continuar em
execução exatamente no mesmo ponto no tempo em que foi criado o ponto de
verificação.
Essa funcionalidade requer o [CRIU 3.11](https://www.criu.org/) ou posterior
instalado no sistema.

Para criar um ponto de verificação do contêiner, use:

```bash
sudo podman container checkpoint <container_id>
```

## Restaurando o contêiner

A restauração de um contêiner só é possível a partir de um ponto de verificação
previamente salvo de um contêiner.
O contêiner restaurado continuará em execução exatamente no mesmo ponto no tempo
em que foi salvo.

Para restaurar o contêiner, use:

```bash
sudo podman container restore <container_id>
```

Após ser restaurado, o contêiner voltará a responder às solicitações como antes
do checkpoint.

```bash
curl http://<endereço-ip>:8080
```

## Migrando o contêiner

Para migrar um contêiner de um host para outro em tempo real, é criado um ponto
de verificação do contêiner no sistema de origem da migração, transferido para o
sistema de destino e, em seguida, restaurado no sistema de destino.
Ao transferir o ponto de verificação, é possível especificar um arquivo de
saída.

No sistema de origem:

```bash
sudo podman container checkpoint <container_id> -e /tmp/checkpoint.tar.zst
scp /tmp/checkpoint.tar.zst <destination_system>:/tmp
```

No sistema de destino:

```bash
sudo podman container restore -i /tmp/checkpoint.tar.zst
```

Após ser restaurado, o contêiner voltará a responder às solicitações como antes
do checkpoint.
Desta vez, o contêiner continuará em execução no sistema de destino.

```bash
curl http://<endereço-ip>:8080
```
