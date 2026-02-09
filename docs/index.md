---
# Copyright (c) 2026 Podman Container Tools, a Series of LF Projects, LLC.
# Podman Container Tools™ is a trademark of LF Projects, LLC.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/containers/podman/blob/-/LICENSE

source_url: https://github.com/containers/podman.io/blob/main/docs/index.md
revision: 8d873f886942055b791c64678568b0cf2d6f0ec9
status: ready

id: podman
title: Começando com o Podman
---

![Logo do Podman](/logos/raw/podman-logo-orig.png#gh-light-mode-only)![Logo do Podman](/logos/raw/podman-logo-dark.png#gh-dark-mode-only)

# Primeiros passos com o Podman

O Podman é um utilitário fornecido como parte da biblioteca libpod.
Ele pode ser usado para criar e manter contêineres.
O tutorial a seguir ensinará como configurar o Podman e executar alguns comandos
básicos.

## Documentação do Podman

A documentação do Podman está localizada [aqui](https://docs.podman.io).

## Instalando o Podman

Para instalar ou compilar o Podman, consulte as
[instruções de instalação](docs/installation).

## Familiarizando-se com o Podman

Os exemplos de código foram projetados para serem executados como um usuário sem
privilégios de root e utilizam o comando `sudo` quando a elevação de privilégios
para root for necessária.

### Obtendo ajuda

Para obter ajuda e descobrir como o Podman funciona, você pode usar o comando
_help_:

```bash
podman --help
podman <subcomando> --help
```

Para obter mais detalhes, você pode consultar as páginas de manual:

```bash
man podman
man podman-<subcomando>
```

Consulte também o
[Guia de solução de problemas do Podman](https://github.com/containers/podman/blob/main/troubleshooting.md)
para encontrar problemas conhecidos e dicas sobre como resolver erros comuns de
configuração.

### Pesquisando, baixando e listando imagens

O Podman pode pesquisar imagens em registros remotos com algumas palavras-chave
simples.

```bash
podman search <termo-de-busca>
```

Você também pode refinar sua busca com filtros:

```bash
podman search httpd --filter=is-official
```

Baixar uma imagem também é fácil.

```bash
podman pull docker.io/library/httpd
```

Após baixar algumas imagens, você pode listar todas as imagens presentes em seu
computador.

```bash
podman images
```

**Nota:** O Podman pesquisa em diferentes registros.
Portanto, recomenda-se usar o nome completo da imagem (_docker.io/library/httpd_
em vez de _httpd_) para garantir que você esteja usando a imagem correta.

### Executando um contêiner

Este contêiner de exemplo executará um servidor httpd muito básico que serve
apenas sua página inicial.

```bash
podman run -d -p 8080:80/tcp docker.io/library/httpd
```

**Nota**: Como o contêiner está sendo executado em modo desanexado, representado
pelo parâmetro `-d` no comando `podman run`, o Podman exibirá o ID do contêiner
após a execução do comando.

**Nota**: Usamos encaminhamento de portas para acessar o servidor HTTP.
Para funcionar corretamente, é necessário pelo menos o slirp4netns v0.3.0.

### Listando contêineres em execução

O comando `podman ps` é usado para listar os contêineres criados e em execução.

```bash
podman ps
```

**Nota:** Se você adicionar `-a` ao comando `podman ps`, o Podman exibirá todos
os contêineres (criados, finalizados, em execução etc.).

### Testando o contêiner httpd

Como você pode ver, o contêiner não possui um endereço IP atribuído.
O contêiner está acessível através da porta publicada em sua máquina local.

```bash
curl http://localhost:8080
```

A partir de outra máquina, você precisa usar o endereço IP do host que executa o
contêiner.

```bash
curl http://<endereço-ip>:8080
```

**Nota:** Em vez de usar curl, você também pode apontar um navegador para
`http://localhost:8080`.

### Inspecionando um contêiner em execução

Você pode "inspecionar" um contêiner em execução para obter metadados e detalhes
sobre ele.
O comando `podman inspect` fornecerá muitas informações úteis, como variáveis de
ambiente, configurações de rede ou recursos alocados.

Como o contêiner está sendo executado no modo **sem privilégios de root**,
nenhum endereço IP é atribuído a ele.

```bash
podman inspect -l | grep IPAddress
            "IPAddress": "",
```

**Nota:** O argumento `-l` é argumento de conveniência para selecionar o
**contêiner mais recente**.
Você também pode usar o ID ou o nome do contêiner em vez de `-l` ou o argumento
longo `--latest`.

**Nota**: Se você estiver executando um cliente Podman remoto, incluindo
máquinas Mac e Windows (exceto WSL2), a opção `-l` não estará disponível.

### Visualizando os logs do contêiner

Você também pode visualizar os logs do contêiner com o Podman:

```bash
podman logs -l

127.0.0.1 - - [04/May/2020:08:33:48 +0000] "GET / HTTP/1.1" 200 45
127.0.0.1 - - [04/May/2020:08:33:50 +0000] "GET / HTTP/1.1" 200 45
127.0.0.1 - - [04/May/2020:08:33:51 +0000] "GET / HTTP/1.1" 200 45
127.0.0.1 - - [04/May/2020:08:33:51 +0000] "GET / HTTP/1.1" 200 45
127.0.0.1 - - [04/May/2020:08:33:52 +0000] "GET / HTTP/1.1" 200 45
127.0.0.1 - - [04/May/2020:08:33:52 +0000] "GET / HTTP/1.1" 200 45
```

### Visualizando os PIDs do contêiner

Você pode observar o PID do httpd no contêiner com o comando `podman top`.

```bash
podman top -l

USER     PID   PPID   %CPU    ELAPSED            TTY     TIME   COMMAND
root     1     0      0.000   22m13.33281018s    pts/0   0s     httpd -DFOREGROUND
daemon   3     1      0.000   22m13.333132179s   pts/0   0s     httpd -DFOREGROUND
daemon   4     1      0.000   22m13.333276305s   pts/0   0s     httpd -DFOREGROUND
daemon   5     1      0.000   22m13.333818476s   pts/0   0s     httpd -DFOREGROUND
```

### Interrompendo o contêiner

Você pode interromper o contêiner:

```bash
podman stop -l
```

Você pode verificar o status de um ou mais contêineres usando o comando
`podman ps`.
Nesse caso, você deve usar o argumento `-a` para listar todos os contêineres.

```bash
podman ps -a
```

### Removendo o contêiner

Finalmente, você pode remover o contêiner:

```bash
podman rm -l
```

Você pode verificar a exclusão do contêiner executando `podman ps -a`.

## Rede

Para um guia mais detalhado sobre redes e DNS em contêineres, consulte o
[guia de rede](https://github.com/containers/podman/blob/main/docs/tutorials/basic_networking.md).

## Ponto de verificação, migração e restauração de contêineres

Criar um ponto de verificação em um contêiner o interrompe enquanto grava o
estado de todos os processos no contêiner em disco.
Com isso, um contêiner pode ser posteriormente migrado e restaurado, executando
exatamente no mesmo ponto no tempo do ponto de verificação.
Para mais detalhes, consulte as
[instruções do ponto de verificação](docs/checkpoint).

## Testes de integração

Para obter mais informações sobre como configurar e executar os testes de
integração em seu ambiente, consulte o arquivo
[README.md](https://github.com/containers/podman/blob/main/test/README.md) dos
testes de integração.

## Documentação do Podman Python

A documentação do SDK do Podman Python está localizada
[aqui](https://podman-py.readthedocs.io/en/latest/index.html).

## Mais informações

Para obter mais informações sobre o Podman e seus subcomandos, consulte as
demonstrações em ASCII na página
[README.md](https://github.com/containers/podman/blob/main/commands-demo.md).
