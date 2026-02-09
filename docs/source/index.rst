..
  Copyright (c) 2026 Podman Container Tools, a Series of LF Projects, LLC.
  Podman Container Tools™ is a trademark of LF Projects, LLC.

  Documentation licensed under the Apache License, Version 2.0.
  The original work was translated from English into Brazilian Portuguese.
  https://github.com/containers/podman/blob/-/LICENSE

  source_url: https://github.com/containers/podman/blob/v5.8/docs/source/index.rst
  revision: da899b92dab93bf4cd373f7b3636cc9bae54ec37
  status: ready

.. include:: includes.rst

O que é o Podman?
=================

O Podman_ é uma ferramenta nativa do Linux, de código aberto e sem daemon,
projetada para facilitar a localização, execução, construção, compartilhamento e
implantação de aplicações usando `contêineres`_ e `imagens de contêiner`_ da
Open Container Initiative (OCI_).
O Podman fornece uma interface de linha de comando (CLI) familiar para qualquer
pessoa que já tenha usado a `Docker Contêiner Engine`_.
A maioria das pessoas usuárias pode simplesmente criar um alias do Docker para o
Podman (`alias docker=podman`) sem problemas.
Semelhante a outras `engines de contêiner`_ comuns (Docker, CRI-O, containerd),
o Podman depende de um tempo de execução de contêiner compatível com OCI (runc,
crun, runv, etc.) para interagir com o sistema operacional e criar os
contêineres em execução.
Isso torna os contêineres em execução criados pelo Podman praticamente
indistinguíveis daqueles criados por qualquer outra engine de contêiner comum.

Os contêineres controlados pelo Podman podem ser executados pelo usuário root ou
por um usuário sem privilégios.
O Podman gerencia todo o ecossistema de contêineres, incluindo pods,
contêineres, imagens de contêineres e volumes de contêineres, utilizando a
biblioteca libpod_.
O Podman é especializado em todos os comandos e funções que auxiliam na
manutenção e modificação de imagens de contêineres OCI, como o download e a
criação de tags.
Ele permite criar, executar e manter esses contêineres e imagens de contêineres
em um ambiente de produção.

Existe uma API RESTful para gerenciar contêineres.
Também temos um cliente Podman remoto que pode interagir com o serviço RESTful.
Atualmente, oferecemos suporte a clientes em Linux, Mac e Windows.
O serviço RESTful é compatível apenas com Linux.

Se você é completamente iniciante em contêineres, recomendamos que consulte a
:doc:`Introdução`.
Para pessoas usuárias avançadas ou aquelas que vêm do Docker, consulte nossos
:doc:`Tutoriais`.
Para pessoas usuárias avançadas e colaboradoras, você pode obter informações
detalhadas sobre a CLI do Podman consultando nossa página de :doc:`Comandos`.
Por fim, para pessoas desenvolvedoras que desejam saber como interagir com a API
do Podman, consulte nossa :doc:`Referência` da documentação da API.

.. toctree::
   :maxdepth: 2
   :caption: Conteúdo:

   Introdução
   :doc:`<markdown/podman.1>` Ferramenta simples de gerenciamento para pods,
     contêineres e imagens.
   Comandos
   Referência
   Tutoriais
   Pesquisa
   Podman Python <https://podman-py.readthedocs.io/en/latest/>
