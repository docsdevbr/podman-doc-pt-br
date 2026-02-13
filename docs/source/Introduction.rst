..
  Copyright (c) 2026 Podman Container Tools, a Series of LF Projects, LLC.
  Podman Container Tools™ is a trademark of LF Projects, LLC.

  Documentation licensed under the Apache License, Version 2.0.
  The original work was translated from English into Brazilian Portuguese.
  https://github.com/containers/podman/blob/-/LICENSE

  source_url: https://github.com/containers/podman/blob/v5.8/docs/source/Introduction.rst
  revision: 7c9aa72c554708ec022dcdf89fc9b5ef4cc44355
  status: ready

.. include:: includes.rst

Introdução
==========

Os contêineres_ simplificam a produção, distribuição, descoberta e uso de
aplicações com todas as suas dependências e arquivos de configuração padrão.
As pessoas usuárias podem testar ou implantar uma nova aplicação com um ou dois
comandos, em vez de seguir páginas de instruções de instalação.
Veja como encontrar sua primeira `imagem de contêiner`_::

    podman search docker.io/busybox

Saída::

    NAME                                         DESCRIPTION
    docker.io/library/busybox                    Busybox base image.
    docker.io/rancher/busybox
    docker.io/openebs/busybox-client
    docker.io/antrea/busybox
    docker.io/hugegraph/busybox                  test image
    ...

O comando anterior retornou uma lista de imagens de contêiner disponíveis
publicamente no Docker Hub.
Essas imagens de contêiner são fáceis de usar, mas apresentam diferentes níveis
de qualidade e manutenção.
Vamos usar a primeira da lista, pois parece estar bem mantida.

Para executar a imagem de contêiner busybox, basta um único comando::

    podman run -it docker.io/library/busybox

Saída::

    / #

Você pode explorar o contêiner busybox por um tempo, mas logo perceberá que
executar um contêiner pequeno com alguns utilitários Linux oferece pouco valor,
então saia dele::

    exit

Há um ditado antigo que diz "ninguém usa um sistema operacional só por usar", e
o mesmo se aplica aos contêineres.
O interessante e valioso é a carga de trabalho executada sobre um sistema
operacional ou em um contêiner.

Às vezes, encontramos uma imagem de contêiner disponível publicamente para a
carga de trabalho exata que procuramos, e ela já estará empacotada exatamente
como queremos.
Mas, na maioria das vezes, há algo que queremos adicionar, remover ou
personalizar.
Pode ser algo simples como uma configuração de segurança ou desempenho, ou algo
complexo como adicionar uma carga de trabalho complexa.
De qualquer forma, os contêineres facilitam bastante a realização das alterações
necessárias.

As imagens de contêiner não são, na verdade, imagens.
São repositórios, geralmente compostos por múltiplas camadas.
Essas camadas podem ser facilmente adicionadas, salvas e compartilhadas com
outras pessoas usando um arquivo Containerfile_ (Dockerfile).
Esse arquivo único geralmente contém todas as instruções necessárias para criar
uma nova imagem de contêiner e pode ser facilmente compartilhado publicamente
usando ferramentas como o GitHub.

Aqui está um exemplo de como criar uma imagem de contêiner a partir de conteúdo
que reside em um repositório git::

    podman build -t hello https://github.com/containers/PodmanHello.git

Assim que a criação da imagem for concluída, é fácil executar a nova imagem a
partir do nosso cache local::

    podman run -it hello

Saída::

    !... Hello Podman World ...!

             .--"--.
           / -     - \
          / (O)   (O) \
       ~~~| -=(,Y,)=- |
        .---. /`  \   |~~
     ~/  o  o \~~~~.----. ~~
      | =(X)= |~  / (O (O) \
       ~~~~~~~  ~| =(Y_)=-  |
      ~~~~    ~~~|   U      |~~

    Project:   https://github.com/containers/podman
    Website:   https://podman.io
    Desktop:   https://podman-desktop.io
    Documents: https://docs.podman.io
    YouTube:   https://youtube.com/@Podman
    X/Twitter: @Podman_io
    Mastodon:  @Podman_io@fosstodon.org

Criar novas imagens é ótimo, mas compartilhar nosso trabalho com outras pessoas
permite que elas revisem nosso trabalho, critiquem a forma como as criamos e
ofereçam versões aprimoradas.
Nossa imagem `hello` recém-criada pode ser publicada em quay.io ou docker.io
para compartilhá-la com o mundo.
Tudo o que é necessário para executar a aplicação `hello` está incluído na
imagem do contêiner.
Outras pessoas podem baixá-la e usá-la facilmente, ou fazer melhorias nela.

A padronização de imagens de contêiner e `registros de contêiner`_ possibilita
um novo nível de colaboração por meio do consumo simplificado.
Esse modelo de consumo simplificado é possível porque todos os principais
mecanismos de contêineres e servidores de registro usam o formato da Open
Containers Initiative (OCI_).
Isso permite que as pessoas usuárias encontrem, executem, criem, compartilhem e
implantem contêineres onde quiserem.
O Podman e outras `engines de contêiner`_, como CRI-O, Docker ou containerd,
podem criar e consumir imagens de contêineres do docker.io, quay.io, de um
registro local ou até mesmo de um registro fornecido por um provedor de nuvem.
O formato de imagem OCI facilita esse ecossistema por meio de um padrão único.

Por exemplo, se quiséssemos compartilhar nossa imagem de contêiner `hello`
recém-criada no quay.io, seria fácil.
Primeiro, faça login no quay::

    podman login quay.io

Entrada::

    Username: <usuário>
    Password: ********
    Login Succeeded!

Em seguida, crie uma tag da imagem para que possamos publicá-la em nossa conta
de usuário::

    podman tag localhost/hello quay.io/USERNAME/hello

Por fim, clique na imagem::

    podman push quay.io/USERNAME/hello

Saída::

    Getting image source signatures
    Copying blob bf62b9b17289 done   |
    Copying config 17a4bf5a30 done   |
    Writing manifest to image destination

Observe que adicionamos uma camada ao nosso registro e agora ela está disponível
para outras pessoas compartilharem.
Dê uma olhada rápida::

    podman inspect quay.io/USERNAME/hello

Saída::

    [
        {
            "Id": "17a4bf5a301a374771ac66dd09c33d1d765af5265d20d6b4da7ac578381efd87",
            "Digest": "sha256:ee693991b0c8c8c12dfe0e90c25db1b73867e672478fd7a187a2fae31f72531a",
            "RepoTags": [
                "quay.io/USERNAME/hello:latest",
    ...

Em resumo, o Podman facilita a busca, execução, criação e compartilhamento de
imagens.

* Encontre: seja para encontrar uma imagem no dockerhub.io ou quay.io, em um
  servidor de registro interno ou diretamente de um fornecedor, alguns comandos
  `podman search`_ e `podman pull`_ tornam tudo fácil.
* Execute: é fácil usar imagens pré-construídas com tudo o que é necessário para
  executar uma aplicação completa ou começar a partir de uma imagem base de
  distribuição Linux com o comando `podman run`_.
* Crie: criar novas camadas com pequenos ajustes ou grandes reformulações é
  fácil com `podman build`_.
* Compartilhe: o Podman permite que você envie suas imagens recém-criadas para
  onde quiser com um único comando `podman push`_.

Para obter mais instruções sobre casos de uso, consulte nossa página de
:doc:`Tutoriais`.
