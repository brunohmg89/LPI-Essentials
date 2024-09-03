# LPI Essentials - LinuxTips

## Day 2

- `ssh USUARIO@IP-OU-NOME-MAQUINA`
- Verificando que você realmente está acessando outra máquina `cat /etc/debian_version` esse comando mostra a versão do Debian que está instalado
- `USUARIO@SERVIDOR:~$` - `~` simboliza o diretório home do usuário `/home/USUARIO`
- `USUARIO@SERVIDOR:~$` - `$` simboliza que quem está logado não é administrador do sistema, usuário comum.
- `su - ` "su" significa "super user" para se tornar root/administrador do sistema
- `root@SERVIDOR:~#` - diretório do usuário root `/root`
- `root@SERVIDOR:~#` - `#` simboliza que quem está logado é root/administrador do sistema
- `history` serve para trazer um histórico de comandos utilizados

- Shell: componente de interação com o sistema operacional

- Diretório é o local onde se armazena outros diretórios e arquivos

- LSB - Linux Standard Basic: Traz um padrão entre as distribuições Linux

- FHS - File System Hierarchy Standard

- Estrutura básica de diretórios:
    - BIN: `/bin` Binários de usuários, essenciais no boot.
    - BOOT: `/boot` Arquivo do gerenciador de partida e kernel, símbolos.
    - DEV: `/dev` Dispositivos do sistema
        - sda: primeiro disco fisico
            - sda1: primeira partição primária
            - sda2: segunda partição primária (no máximo 4)
            - sda5: partição lógica, subdivisões de uma partição primária que desse caso seria do sda1. E assim por diante. 
        - sdb - segundo disco fisico e assim por diante
        - Diferença entre arquivos
            - `-rwxrwxrwx` - arquivos com `-` no inicio são arquivos comuns com informação
            - `drwxrwxrwx` - arquivos com `d` no inicio são diretórios
            - `lrwxrwxrwx` - arquivos com `l` no inicio são links/atalhos para outros arquivos
            - `brwxrwxrwx` - arquivos com `b` no inicio são arquivos de bloco, discos em geral como HDs e pendrives
            - `crwxrwxrwx` - arquivos com `c` no inicio são arquivos de caractere que trafegam informação como terminal(tty)
    - ETC: `/etc` Arquivos de configuração globais.
        - `/etc/opt` Arquivos de configuração para aplicativos em /opt
        - `/etc/X11` Arquivos de configuração para o X Window System 11
    - HOME: `/home` Armazenamento de dados de contas de usuários normais.
    - LIB - LIB64 - LIB32 - LIBX32: `/lib` Bibliotecas essenciais do sistema, de binários localizados em `/bin` e `/sbin`.
    - LOST+FOUND: `/lost+found` Diretório de "achados e perdidos" esse diretório aparece em vários outros e é responsável por recuperar arquivos, por exemplo, com uma queda de energia.
    - MEDIA: `/media` Ponto de montagem de mídias removíveis (como pen-drives, cd-rom).
    - MNT: `/mnt` Sistema de arquivos montado temporariamente.
    - OPT: `/opt` Pacotes estático de aplicações.
    - PROC: `/proc` Sistema de arquivos virtual, onde pode fazer a interação com o kernel e processos do sistema.
    - ROOT: `/root` Armazenamento de dados de contas do superusuário.
    - RUN: `/run` Diretório com arquivos que contém informações virtuais dinamicos de "coisas" que estão rodando no sistema.
    - SBIN: `/sbin` Binários do superusuário, essenciais no boot.
    - SRV: `/srv` Diretório que deveria conter arquivos/informações estáticos, como páginas HTTP de um web server
    - SYS: `/sys` Diretório que contém arquivo/informações "quentes" do sistema mais voltados aos devices.
    - TMP: `/tmp` Arquivos temporários. Conteúdo geralmente apagado no reboot nas distribuições.
    - USR: `/usr` (unix system resources) - Hierarquia secundária (não essenciais no boot) para dados compartilhados de usuários.
        - `/usr/bin` O mesmo que a hierarquia /bin, mas contém binários não essenciais ao funcionamento da máquina ou para o recovery.
        - `/usr/include` Diretório padrãod para headers.
        - `/usr/lib` O mesmo que a hierarquia /lib, mas não essenciais ao boot
        - `/usr/sbin` O mesmo que o /sbin, mas não essenciais ao boot da máquina
        - `/usr/share` Dados compartilhados independentes de arquitetura
        - `/usr/src` Armazenamento de código fonte da máquina
        - `/usr/X11R6` X Window Sysem, versão 11R6
        - `/usr/local` Armazenamento de binários não distribuidos na instalação principal da máquina, ou seja, fora do sistema de empacotamento. Também é o local de armazenamento terciário de dados.
    - VAR: `/var` Arquivos que são gravados com frequência (logs, páginas web, email, imagens, etc).
        - `/var/lock` Arquivos de lock, usados para controlar corretamente os recursos em uso
        - `/var/log` Arquivos de log, usado para logs em geral
        - `/var/mail` Caixas de e-mail dos usuários do sistema em formato mailbox
        - `/var/run` Contém dados sobre a execução do sistema desde seu primeiro boot (daemons e usuários)
        - `/var/spool` Spooling de tarefas (fila de impressão, cache de pacotes, proxy, etc)
        - `/var/spool/mail` Antigo local da caixa de correio de usuários (deve ser usado /var/mail)
        - `/var/tmp` Arquivos temporários. Quando usado em modo multi-usuário.

### Questões

1. O que é o Shell?

    :black_large_square: Uma marca de posto de combustiveis
 
    :white_check_mark: Interface entre o usuário e o sistema
 
    :black_large_square: Interface entre o kernel e o usuário
 
    :black_large_square: Interface entre o bash e o X

---

2. Como eu programo o desligamento de uma máquina para daqui 10 minutos?
 
    :black_large_square: shutdown -h -schedule 10
 
    :black_large_square: shutdown -h now +10
 
    :white_check_mark: shutdown -h +10
 
    :black_large_square: shutdown -r +10

---

3. Qual é o diretório padrão para arquivos de configuração?
 
    :black_large_square: sbin
 
    :black_large_square: /bin
 
    :black_large_square: /usr
 
    :white_check_mark: /etc
 
    :black_large_square: /

---

4. Qual é o único usuário que não possui o seu diretório "home" no `/home`?

    :black_large_square: jeferson

    :black_large_square: superuser

    :white_check_mark: root

    :black_large_square: todos que não logaram nos ultimos dias

---

5. Quais são os diretórios com binários de uso exclusivo do root?

    :black_large_square: /bin

    :white_check_mark: /sbin

    :black_large_square: /usr

    :white_check_mark: /usr/sbin

    :black_large_square: /tmp/sbin

---

6. Qual é o diretório onde está o arquivo do kernel do Linux?

    :black_large_square: /sbin

    :black_large_square: /bin

    :white_check_mark: /boot

    :black_large_square: /dev

    :black_large_square: /etc

---

7. Quais dispositivos abaixo são dispositivos de bloco?

    :black_large_square: porta paralela

    :white_check_mark: HD

    :white_check_mark: Pendrive

    :white_check_mark: Disco Externo

    :black_large_square: Terminal