---
# Copyright (c) 2026 Podman Container Tools, a Series of LF Projects, LLC.
# Podman Container Tools™ is a trademark of LF Projects, LLC.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/containers/podman/blob/-/LICENSE

source_url: https://github.com/containers/podman.io/blob/main/docs/installation.md
revision: fc29338e636181a07d6b46ac793bde807618f9b4
status: ready

title: Instalação do Podman
---

# Instruções de instalação do Podman

Procurando uma interface gráfica?
Você pode encontrar o Podman Desktop
[aqui](https://podman-desktop.io/downloads).

## Instalando no Mac e Windows

Embora os "contêineres sejam Linux", o Podman também funciona no Mac e no
Windows, onde fornece uma CLI nativa do Podman e incorpora um sistema Linux
convidado para executar seus contêineres.
Esse convidado é chamado de máquina Podman e é gerenciado com o comando
`podman machine`.
O Podman no Mac e no Windows também aceita clientes da API do Docker, permitindo
o uso direto de ferramentas baseadas em Docker e acesso programático a partir da
linguagem de sua escolha.

### macOS

No Mac, cada máquina Podman é executada em uma máquina virtual.
Após a instalação, o comando podman pode ser executado diretamente do shell Unix
no `Terminal`, onde se comunica remotamente com o serviço podman em execução na
máquina virtual.

<details open>
<summary>Baixe o instalador do Podman (recomendado)</summary>

O Podman pode ser baixado do site [Podman.io](https://podman.io).

Também disponibilizamos os instaladores e outros binários em nossa
[página de lançamentos do GitHub](https://github.com/containers/podman/releases).

</details>

Embora não seja recomendado, o Podman também pode ser obtido através do
Homebrew, o gerenciador de pacotes.

<details>
<summary>Instale via Brew</summary>

Como o Brew é um gerenciador de pacotes mantido pela comunidade, não podemos
garantir a estabilidade das instalações do Podman via Brew.
Portanto, a instalação via Brew não é recomendada.

No entanto, se você deseja usar o Brew, primeiro precisa instalar o
[Homebrew](https://brew.sh/).
Depois de configurar o Brew, você pode usar o comando `brew install` para
instalar o Podman:

```bash
brew install podman
```

</details>

Após a instalação, você precisa criar e iniciar sua primeira máquina Podman:

```bash
podman machine init
podman machine start
```

Em seguida, você pode verificar as informações de instalação usando:

```bash
podman info
```

Também disponibilizamos binários e um instalador pkg em nossa
[página de lançamentos do GitHub](https://github.com/containers/podman/releases).

### Windows

No Windows, cada máquina Podman é executada por uma distribuição virtualizada do
Subsistema Windows para Linux (WSLv2).
Após a instalação, o comando podman pode ser executado diretamente do prompt do
Windows PowerShell (ou CMD), onde se comunica remotamente com o serviço podman
em execução no ambiente WSL.
Alternativamente, você pode acessar o Podman diretamente da instância WSL se
preferir um prompt e ferramentas Linux.

Consulte o
[guia do Podman para Windows](https://github.com/containers/podman/blob/main/docs/tutorials/podman-for-windows.md)
para obter instruções de configuração e uso.

## Instalando no Linux

### Distribuições Linux

#### [Arch Linux](https://www.archlinux.org) e [Manjaro Linux](https://manjaro.org)

```bash
sudo pacman -S podman
```

Se você tiver problemas ao executar o Podman no modo
[sem root](https://github.com/containers/podman/blob/main/README.md#rootless),
siga as instruções
[aqui](<https://wiki.archlinux.org/index.php/Linux_Containers#Enable_support_to_run_unprivileged_containers_(optional)>).

Para mais informações sobre o Podman no Arch Linux,
[clique aqui](https://wiki.archlinux.org/title/Podman).

#### [Alpine Linux](https://alpinelinux.org)

```bash
sudo apk add podman
```

Para mais detalhes, consulte as instruções na
[wiki do Alpine Linux](https://wiki.alpinelinux.org/wiki/Podman).

#### [CentOS Stream](https://www.centos.org)

O Podman está disponível por padrão no repositório AppStream para CentOS Stream
9+.

```bash
sudo dnf -y install podman
```

#### [Debian](https://debian.org)

O pacote podman está disponível nos repositórios do Debian 11 (Bullseye) e
versões posteriores.

```bash
sudo apt-get -y install podman
```

#### [Fedora](https://getfedora.org)

```bash
sudo dnf -y install podman
```

Para executar comandos `podman machine ...`:

```bash
sudo dnf -y install podman-machine
```

O slirp4netns não é mais o padrão para redes sem privilégios de root em novas
instalações do podman, tendo sido substituído pelo
[passt](https://passt.top/passt/about/).
Se você tiver contêineres usando o slirp4netns, certifique-se de que o
slirp4netns esteja instalado:

```bash
sudo dnf -y install slirp4netns
```

#### [Fedora CoreOS](https://coreos.fedoraproject.org), [Fedora Silverblue](https://silverblue.fedoraproject.org)

Integrado, sem necessidade de instalação.

#### [Gentoo](https://www.gentoo.org)

```bash
sudo emerge app-containers/podman
```

#### [OpenEmbedded](https://www.openembedded.org)

Receitas Bitbake para Podman e suas dependências estão disponíveis na
[camada meta-virtualização](https://git.yoctoproject.org/cgit/cgit.cgi/meta-virtualization/).
Adicione a camada ao seu ambiente de compilação OpenEmbedded e compile o Podman
usando:

```bash
bitbake podman
```

#### [openSUSE](https://www.opensuse.org)

```bash
sudo zypper install podman
```

#### [openSUSE Kubic](https://kubic.opensuse.org)

Integrado, sem necessidade de instalação.

#### [Raspberry Pi OS arm64 (beta)](https://downloads.raspberrypi.org/raspios_arm64/images/)

O Raspberry Pi OS usa os repositórios padrão do Debian, portanto, é totalmente
compatível com o repositório arm64 do Debian.
Você pode simplesmente seguir os [passos para o Debian](#debian) para instalar o
Podman.

#### [RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux)

Siga a [documentação oficial](https://access.redhat.com/solutions/3650231).

#### [Ubuntu](https://www.ubuntu.com)

O pacote podman está disponível nos repositórios oficiais do Ubuntu 20.10 e
versões mais recentes.

```bash
# Ubuntu 20.10 e versões mais recentes
sudo apt-get update
sudo apt-get -y install podman
```

#### [Linux Mint](https://linuxmint.com)

Siga os passos para Ubuntu (ou Debian, se você usa LMDE).

### Instalando versões de desenvolvimento do Podman

#### [Fedora](https://getfedora.org)

Você pode testar a versão mais recente do Podman no repositório
`updates-testing` do Fedora antes que ela seja disponibilizada para todas as
pessoas usuárias do Fedora.

```bash
sudo dnf update --refresh --enablerepo=updates-testing podman
```

Se você usar um pacote Podman mais recente do repositório `updates-testing` do
Fedora, agradecemos seu feedback com um `+1` no
[Bodhi, sistema de gerenciamento de atualizações do Fedora](https://bodhi.fedoraproject.org/updates/?packages=podman).

### Instalando versões de ponta do Podman

Se você gosta de desafios e tem interesse em testar as versões mais recentes do
Podman, ainda não lançadas, no Fedora, CentOS Stream 9+ e RHEL9+, temos um
[repositório Copr](https://copr.fedorainfracloud.org/coprs/rhcontainerbot/podman-next/).

CUIDADO: Este repositório contém builds rpm gerados usando o branch `main` dos
repositórios de ferramentas de contêiner upstream e NÃO é recomendado para uso
em produção.

Habilite o Copr e instale o Podman.

```bash
sudo dnf copr enable rhcontainerbot/podman-next -y
sudo dnf install podman
```

## Instalando no [FreeBSD](https://freebsd.org)

:::caution

A versão da engine de contêiner Podman para FreeBSD é experimental e deve ser
usada apenas para fins de avaliação e teste.
Ela é compatível com o **FreeBSD 14.3 e versões mais recentes**.

:::

Você pode instalar o Podman no FreeBSD usando o `pkg`:

```bash
pkg install podman
```

Existe também um meta-pacote `podman-suite` que baixará pacotes adicionais para
você (buildah, skopeo).

#### Configuração inicial

Para suportar corretamente a política de reinicialização de contêineres do
Podman, o conmon precisa que o `fdescfs(5)` esteja montado em `/dev/fd`.

Se `/dev/fd` ainda não estiver montado:

```bash
mount -t fdescfs fdesc /dev/fd
```

Para tornar a alteração permanente, adicione a seguinte linha ao arquivo
`/etc/fstab`:

```
fdesc   /dev/fd         fdescfs         rw      0       0
```

Para iniciar o Podman após a reinicialização:

```bash
service podman enable
```

##### Redes

A rede de contêineres depende do NAT para permitir que os pacotes de rede do
contêiner cheguem à rede do host.
Isso requer um firewall PF para realizar a tradução.
Um exemplo simples está incluído - para usá-lo:

```bash
cp /usr/local/etc/containers/pf.conf.sample /etc/pf.conf
```

Edite o arquivo `/etc/pf.conf` e defina as variáveis `v4egress_if` e
`v6egress_if` para suas interfaces de rede.

Habilite e inicie o `pf`:

```
service pf enable
service pf start
```

A configuração de exemplo do PF inclui suporte para redirecionamento de portas.
Isso é implementado como regras de redirecionamento em âncoras aninhadas em
cni-rdr.

O suporte para redirecionar conexões do host do contêiner para serviços em
execução em um contêiner está incluído no FreeBSD 13.3 e versões posteriores.
Para habilitar isso, primeiro carregue o módulo do kernel pf e habilite o
suporte do PF para esses redirecionamentos usando o sysctl:

```bash
echo 'pf_load="YES"' >> /boot/loader.conf
kldload pf
sysctl net.pf.filter_local=1
echo 'net.pf.filter_local=1' >> /etc/sysctl.conf.local
service pf restart
```

As regras de redirecionamento funcionarão se o endereço de destino for localhost
(por exemplo, 127.0.0.1 ou ::1) - para habilitar isso, a seguinte linha deve ser
incluída em seu arquivo `/etc/pf.conf`:

```
nat-anchor "cni-rdr/*"
```

Se estiver atualizando de uma versão anterior, isso precisa ser adicionado ao
arquivo `/etc/pf.conf`.

Por exemplo, se a porta 1234 do host for redirecionada para um serviço HTTP em
execução em um contêiner, você poderá se conectar a ele usando:

```bash
fetch -o- http://$(hostname):1234
```

ou

```bash
fetch -o- http://localhost:1234
```

##### Armazenamento

As imagens dos contêineres e seus respectivos estados são armazenados em
`/var/db/containers`.
Recomenda-se o uso do ZFS para isso:

```bash
zfs create -o mountpoint=/var/db/containers zroot/containers
```

Se o seu sistema não suportar ZFS, altere o arquivo `storage.conf` para usar o
driver de armazenamento `vfs`:

```bash
sed -I .bak -e 's/driver = "zfs"/driver = "vfs"/' /usr/local/etc/containers/storage.conf
```

##### Verificação

Após seguir estes passos, você deverá conseguir executar imagens nativas:

```bash
podman run --rm docker.io/dougrabson/hello
```

##### Emulação Linux

É possível executar diversas imagens de contêineres Linux usando a emulação
Linux do FreeBSD:

```bash
sudo sysrc linux_enable=YES
sudo service linux start
sudo podman run --rm --os=linux docker.io/library/alpine cat /etc/os-release | head -1
NAME="Alpine Linux"
```

## Compilando a partir do código-fonte

### Dependências de compilação e execução

**Obrigatório**

No Fedora:

```bash
# Instale as dependências de compilação
sudo dnf -y builddep rpm/podman.spec

# Instale as dependências de execução
sudo dnf -y install catatonit conmon containers-common-extra
```

Em todas as versões do RHEL e CentOS Stream, primeiro instale o `dnf-builddep`:

```bash
sudo dnf -y install 'dnf-command(builddep)'
```

Instale as dependências de compilação:

```bash
# CentOS Stream 9+
sudo dnf -y builddep rpm/podman.spec --enablerepo=crb

# RHEL 9+
sudo dnf -y builddep rpm/podman.spec --enablerepo=codeready-builder-for-rhel-$(rpm --eval %{?rhel})-$(uname -m)-rpms
```

Instale as dependências de tempo de execução:

```bash
sudo dnf -y install \
  conmon \
  containers-common \
  crun \
  iptables \
  netavark \
  nftables \
  slirp4netns
```

Debian, Ubuntu e distribuições relacionadas:

```bash
sudo apt-get install \
  btrfs-progs \
  gcc \
  git \
  golang-go \
  go-md2man \
  iptables \
  libassuan-dev \
  libbtrfs-dev \
  libc6-dev \
  libdevmapper-dev \
  libglib2.0-dev \
  libgpgme-dev \
  libgpg-error-dev \
  libprotobuf-dev \
  libprotobuf-c-dev \
  libseccomp-dev \
  libselinux1-dev \
  libsystemd-dev \
  make \
  netavark \
  passt \
  pkg-config \
  runc \
  uidmap
```

O pacote `netavark` pode não estar disponível em versões mais antigas do
Debian/Ubuntu.
Instale o pacote `containernetworking-plugins` em vez disso.

No openSUSE Leap 15.x e Tumbleweed:

```bash
sudo zypper -n in libseccomp-devel libgpgme-devel libbtrfs-devel make man
```

No Manjaro (e talvez outras distribuições Linux):

Certifique-se de que o kernel Linux suporte namespaces de usuário:

```
> zgrep CONFIG_USER_NS /proc/config.gz
CONFIG_USER_NS=y

```

Caso contrário, atualize o kernel.
Para o Manjaro Linux, as instruções podem ser encontradas aqui:
https://wiki.manjaro.org/index.php/Manjaro_Kernels.

Depois disso, habilite os namespaces de usuário:

```
sudo sysctl kernel.unprivileged_userns_clone=1
```

Para habilitar os namespaces de usuário permanentemente:

```
echo 'kernel.unprivileged_userns_clone=1' | sudo tee /etc/sysctl.d/userns.conf > /dev/null
```

### Construindo dependências ausentes

Se alguma dependência não puder ser instalada ou não estiver suficientemente
atualizada, ela precisará ser compilada a partir do código-fonte.
Isso afetará principalmente o Debian, Ubuntu e distribuições relacionadas, ou o
RHEL onde nenhuma assinatura estiver ativa (por exemplo, VMs na nuvem).

#### Go

Certifique-se de que a versão do Go seja recente o suficiente (ou seja,
`go version`).
Em agosto de 2025, a versão mínima exigida era 1.23.x ou superior.
A versão mínima exigida pode ser encontrada no arquivo
[go.mod](https://github.com/containers/podman/blob/main/go.mod).
Se necessário, os kits do Go estão disponíveis em https://golang.org/dl/.
Como alternativa, o Go pode ser compilado a partir do código-fonte da seguinte
forma (é útil manter o system-go instalado para evitar a necessidade de
[inicializar o go](https://golang.org/doc/install/source):

```bash
export GOPATH=~/go
git clone https://go.googlesource.com/go $GOPATH
cd $GOPATH
cd src
./all.bash
export PATH=$GOPATH/bin:$PATH
```

#### conmon

Espera-se que a versão mais recente do `conmon` esteja instalada no sistema.
O conmon é usado para monitorar os tempos de execução do OCI.
Para compilar a partir do código-fonte, use o seguinte:

```bash
git clone https://github.com/containers/conmon
cd conmon
export GOCACHE="$(mktemp -d)"
make
sudo make podman
```

#### crun / runc

Espera-se que a versão mais recente de pelo menos um ambiente de execução de
contêineres esteja instalada no sistema.
`crun` ou `runc` são algumas das possibilidades, e um deles é escolhido como o
ambiente de execução padrão pelo Podman (crun tem prioridade sobre runc).
Versões compatíveis de `crun` e `runc` estão disponíveis em distribuições Linux
modernas, como o Ubuntu 22.04 ou mais recentes.
A versão mínima necessária para `runc` é a v1.1.11 e para `crun` é a v1.14.3.
Esse requisito é necessário, pois o Podman agora depende de recursos e
comportamentos introduzidos nesta versão.

Para confirmar, a primeira linha da saída de `runc --version` deve mostrar
`version 1.1.11` ou mais recente.
Caso contrário, você pode compilá-lo a partir do código-fonte:

```bash
git clone https://github.com/opencontainers/runc.git $GOPATH/src/github.com/opencontainers/runc
cd $GOPATH/src/github.com/opencontainers/runc
make BUILDTAGS="selinux seccomp"
sudo cp runc /usr/bin/runc
```

#### Adicione a configuração

```bash
sudo mkdir -p /etc/containers
sudo curl -L -o /etc/containers/registries.conf https://raw.githubusercontent.com/containers/image/main/registries.conf
sudo curl -L -o /etc/containers/policy.json https://raw.githubusercontent.com/containers/image/main/default-policy.json
```

#### Pacotes opcionais

A instalação do `fuse-overlayfs` pode resolver diversos problemas, como o do
Ecryptfs:
`configure storage: 'overlay' is not supported over ecryptfs, a mount_program is required: backing file system is unsupported for this graph driver`.

Fedora, CentOS, RHEL e distribuições relacionadas:

```bash
sudo dnf install -y \
  fuse-overlayfs
```

Debian, Ubuntu e distribuições relacionadas:

```bash
sudo apt-get install -y \
  libapparmor-dev \
  fuse-overlayfs
```

O pacote `fuse-overlayfs` também pode ser instalado a partir do
[código-fonte](https://github.com/containers/fuse-overlayfs).

### Obter o código-fonte

Primeiro, certifique-se de que a `go version` encontrada em primeiro lugar no
$PATH seja 1.23.x ou superior.
As instruções [acima](#golang) ajudarão você a compilar uma versão mais recente
do Go, se necessário.
Em seguida, podemos compilar o Podman:

```bash
git clone https://github.com/containers/podman/
cd podman
make BUILDTAGS="selinux seccomp" PREFIX=/usr
sudo env PATH=$PATH make install PREFIX=/usr
```

#### Tags de compilação

Caso contrário, se você não quiser compilar o Podman com suporte a seccomp ou
selinux, você pode adicionar `BUILDTAGS=""` ao executar o comando make.

```bash
make BUILDTAGS=""
sudo make install
```

O Podman suporta tags de compilação opcionais para suporte a vários recursos.
Para adicionar tags de compilação à opção make, a variável `BUILDTAGS` deve ser
definida, por exemplo:

```bash
make BUILDTAGS='seccomp apparmor'
```

Se você estiver compilando no RHEL8, precisará compilar sem suporte ao btrfs
devido à
[sua remoção](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/8/html/considerations_in_adopting_rhel_8/file-systems-and-storage_considerations-in-adopting-rhel-8#btrfs-has-been-removed_file-systems-and-storage):

```
make BUILDTAGS="btrfs_noversion exclude_graphdriver_btrfs"
```

| Tag de compilação                 | Recurso                                     | Dependência |
|-----------------------------------|---------------------------------------------|-------------|
| apparmor                          | Suporte a apparmor.                         | libapparmor |
| cni                               | Rede CNI.                                   |             |
| exclude_graphdriver_btrfs         | Exclui btrfs.                               | libbtrfs    |
| exclude_graphdriver_devicemapper  | Exclui device-mapper.                       | libdm       |
| libdm_no_deferred_remove          | Exclui remoção adiada em libdm.             | libdm       |
| seccomp                           | Filtragem de chamadas de sistema.           | libseccomp  |
| selinux                           | Rotulagem de processos e montagens SELinux. |             |
| systemd                           | Registro de logs do journald.               | libsystemd  |

Observe que o Podman não oferece suporte oficial ao device-mapper.
Portanto, a tag `exclude_graphdriver_devicemapper` é obrigatória.

### Gerenciamento de dependências

Este projeto utiliza [módulos Go](https://github.com/golang/go/wiki/Modules)
para gerenciamento de dependências.
Se o CI reclamar que um pull request deixou um estado inconsistente, é muito
provável que esteja correto.
Após alterar as dependências, certifique-se de executar `make vendor` para
sincronizar o código com o módulo Go e repopular o diretório `./vendor`.

## Ansible

Uma [Role do Ansible](https://github.com/alvistack/ansible-role-podman) também
está disponível para automatizar a instalação do binário estaticamente vinculado
acima em seu sistema operacional compatível:

```bash
sudo su -
mkdir -p ~/.ansible/roles
cd ~/.ansible/roles
git clone https://github.com/alvistack/ansible-role-podman.git podman
cd ~/.ansible/roles/podman
pip3 install --upgrade --ignore-installed --requirement requirements.txt
molecule converge
molecule verify
```

## Arquivos de configuração

### [registries.conf](https://raw.githubusercontent.com/containers/image/main/registries.conf)

#### Página do manual: [registries.conf.5](https://github.com/containers/image/blob/main/docs/containers-registries.conf.5.md)

`/etc/containers/registries.conf`

`registries.conf` é o arquivo de configuração que especifica quais registros de
contêineres devem ser consultados ao completar nomes de imagens que não incluem
um registro ou domínio.

NOTA: No macOS ou Windows, execute o comando `podman machine ssh` para acessar a
máquina virtual e edite o arquivo `/etc/containers/registries.conf` com o mesmo
conteúdo de configuração.
Se encontrar problemas de permissão, execute `podman machine set --rootful` e
tente novamente.

#### Exemplo do pacote `containers-common` do Fedora

```
$ cat /etc/containers/registries.conf
# For more information on this configuration file, see containers-registries.conf(5).
#
# NOTE: RISK OF USING UNQUALIFIED IMAGE NAMES
# We recommend always using fully qualified image names including the registry
# server (full dns name), namespace, image name, and tag
# (e.g., registry.redhat.io/ubi8/ubi:latest). Pulling by digest (i.e.,
# quay.io/repository/name@digest) further eliminates the ambiguity of tags.
# When using short names, there is always an inherent risk that the image being
# pulled could be spoofed. For example, a user wants to pull an image named
# `foobar` from a registry and expects it to come from myregistry.com. If
# myregistry.com is not first in the search list, an attacker could place a
# different `foobar` image at a registry earlier in the search list. The user
# would accidentally pull and run the attacker's image and code rather than the
# intended content. We recommend only adding registries which are completely
# trusted (i.e., registries which don't allow unknown or anonymous users to
# create accounts with arbitrary names). This will prevent an image from being
# spoofed, squatted or otherwise made insecure.  If it is necessary to use one
# of these registries, it should be added at the end of the list.
#
# # An array of host[:port] registries to try when pulling an unqualified image, in order.
unqualified-search-registries = ["registry.fedoraproject.org", "registry.access.redhat.com", "docker.io"]
#
# [[registry]]
# # The "prefix" field is used to choose the relevant [[registry]] TOML table;
# # (only) the TOML table with the longest match for the input image name
# # (taking into account namespace/repo/tag/digest separators) is used.
# #
# # If the prefix field is missing, it defaults to be the same as the "location" field.
# prefix = "example.com/foo"
#
# # If true, unencrypted HTTP as well as TLS connections with untrusted
# # certificates are allowed.
# insecure = false
#
# # If true, pulling images with matching names is forbidden.
# blocked = false
#
# # The physical location of the "prefix"-rooted namespace.
# #
# # By default, this equal to "prefix" (in which case "prefix" can be omitted
# # and the [[registry]] TOML table can only specify "location").
# #
# # Example: Given
# #   prefix = "example.com/foo"
# #   location = "internal-registry-for-example.net/bar"
# # requests for the image example.com/foo/myimage:latest will actually work with the
# # internal-registry-for-example.net/bar/myimage:latest image.
# location = "internal-registry-for-example.com/bar"
#
# # (Possibly-partial) mirrors for the "prefix"-rooted namespace.
# #
# # The mirrors are attempted in the specified order; the first one that can be
# # contacted and contains the image will be used (and if none of the mirrors contains the image,
# # the primary location specified by the "registry.location" field, or using the unmodified
# # user-specified reference, is tried last).
# #
# # Each TOML table in the "mirror" array can contain the following fields, with the same semantics
# # as if specified in the [[registry]] TOML table directly:
# # - location
# # - insecure
# [[registry.mirror]]
# location = "example-mirror-0.local/mirror-for-foo"
# [[registry.mirror]]
# location = "example-mirror-1.local/mirrors/foo"
# insecure = true
# # Given the above, a pull of example.com/foo/image:latest will try:
# # 1. example-mirror-0.local/mirror-for-foo/image:latest
# # 2. example-mirror-1.local/mirrors/foo/image:latest
# # 3. internal-registry-for-example.net/bar/image:latest
# # in order, and use the first one that exists.
#
# short-name-mode="enforcing"

[[registry]]
location="localhost:5000"
insecure=true
```

### [mounts.conf](https://raw.githubusercontent.com/containers/common/main/pkg/subscriptions/mounts.conf)

`/usr/share/containers/mounts.conf` e, opcionalmente, `/etc/containers/mounts.conf`

Os arquivos mounts.conf especificam diretórios de montagem de volumes montados
automaticamente dentro dos contêineres ao executar os comandos `podman run` ou
`podman build`.
O processo do contêiner pode então usar esse conteúdo.
O conteúdo da montagem do volume não é incluído na imagem final.

Normalmente, esses diretórios são usados para passar segredos ou credenciais
necessárias para que o software do pacote acesse repositórios de pacotes
remotos.

Por exemplo, um arquivo mounts.conf com a linha
"`/usr/share/rhel/secrets:/run/secrets`" terá o conteúdo do diretório
`/usr/share/rhel/secrets` montado em `/run/secrets` dentro do contêiner.
Esse ponto de montagem permite que assinaturas do Red Hat Enterprise Linux do
host sejam usadas dentro do contêiner.

Observe que isso não é uma montagem de volume.
O conteúdo dos volumes é copiado para o armazenamento do contêiner, e não
montado diretamente do host.

#### Exemplo do pacote `containers-common` do Fedora:

```
cat /usr/share/containers/mounts.conf
/usr/share/rhel/secrets:/run/secrets
```

### [seccomp.json](https://raw.githubusercontent.com/containers/common/main/pkg/seccomp/seccomp.json)

`/usr/share/containers/seccomp.json`

O arquivo seccomp.json contém a lista de regras permitidas do Seccomp dentro de
contêineres.
Este arquivo é geralmente fornecido pelo pacote containers-common.

O link acima leva você ao arquivo seccomp.json.

### [policy.json](https://raw.githubusercontent.com/containers/image/main/default-policy.json)

`/etc/containers/policy.json`

#### Página do manual: [policy.json.5](https://github.com/containers/image/blob/main/docs/containers-policy.json.5.md)

#### Exemplo do pacote `containers-common` do Fedora:

```
cat /etc/containers/policy.json
{
    "default": [
        {
            "type": "insecureAcceptAnything"
        }
    ],
    "transports":
        {
            "docker-daemon":
                {
                    "": [{"type":"insecureAcceptAnything"}]
                }
        }
}
```
