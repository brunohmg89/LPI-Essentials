# LPI Essentials - LinuxTips

## Day 1

- Linus Benedict Torvalds: Em 1988, Linus foi admitido na Universidade de Helsinki. No mesmo ano, Andy Tanenbaum traz a público o SO MINIX, um derivativo do Unix para fins didáticos que rodava em computadores pessoais (PCs). No fim dos anos 1980, Linus toma contato com os PCs. Em 1990, Torvalds começa a aprender a linguagem de programação C em seus estudos. Em 1991, Linus compra um PC com um processador Intel 80386. Em 5 de janeiro de 1991, ele compra um Intel 80386-IBM PC antes de receber sua cópia MINIX, que, por sua vez, lhe permitiu começar a trabalhar no que se tornaria o Linux.

- Distribuições Linux
    - Debian
        - Ubuntu
        - Linux Mint
    - Redhat
        - CentOS
        - Suze

- Licenças: Definem os direitos e responsabilidades do uso de ferramentas
    - GPL v2 e v3
    - BSD
    - Apache
    - MIT
    - Creative Commons

- DFSG
    - Redistribuição livre
    - Inclusão de código fonte
    - Permitindo modificações e trabalhos derivados
    - Integridade do código fonte do autor (como um compromisso)
    - Sem discriminação contra pessoas ou grupos
    - Sem discriminação contra campos de atuação, como o uso comercial
    - A licença deve aplicar-se a todos aqueles para quem o programa é redistribuído
    - Licença não deve ser específico para um produto
    - Licença não deve restringir outro software

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
            - `crwxrwxrwx` - arquivos com `b` no inicio são arquivos de caractere que trafegam informação como terminal(tty)
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
    - VAR: `/var` Arquivos que são gravados comf requencia (logs, páginas web, email, imagens, etc).
        - `/var/lock` Arquivos de lock, usados para controlar corretamente os recursos em uso
        - `/var/log` Arquivos de log, usado para logs em geral
        - `/var/mail` Caixas de e-mail dos usuários do sistema em formato mailbox
        - `/var/run` Contém dados sobre a execução do sistema desde seu primeiro boot (daemons e usuários)
        - `/var/spool` Spooling de tarefas (fila de impressão, cache de pacotes, proxy, etc)
        - `/var/spool/mail` Antigo local da caixa de correio de usuários (deve ser usado /var/mail)
        - `/var/tmp` Arquivos temporários. Quando usado em modo multi-usuário.

- Comandos para reiniciar e desligar o Linux
    - `halt` para desligar
    - `reboot` para reiniciar
    - `shutdown -h now` para desligar
    - `shutdown -r now` para reiniciar
    - `poweroff` para desligar
    - `init 0` para desligar
    - `init 6` para reiniciar
    - `shutdown --help` para opções detalhadas para reiniciar ou desligar a máquina
    - `shutdown -h 18:00` para programar o desligamento para as 18h.
    - `shutdown -c` para cancelar o agendamento
    - `shutdown -h +30` para programar de desligar a maquina daqui 30 min
    - `shutdown -r +30 "Mensagem"` para programar um reboot da maquina e mandar uma mensagem aos usuários que estiverem logados.

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

4. Qual é o único usuário que não possui o seu diretório "home" no /home?

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

    :white_check_mark: /boot/

    :black_large_square: /dev/

    :black_large_square: /etc

---

7. Quais dispositivos abaixo são dispositivos de bloco?

    :black_large_square: porta paralela

    :white_check_mark: HD

    :white_check_mark: Pendrive

    :white_check_mark:Disco Externo

    :black_large_square: Terminal

## Day 3

- Comandos internos e externos do shell
    - `which COMANDO` para verificar se o comando está instalado na sua máquina
    - `man bash-builtins` para verificar todos os comandos instalados no bash
    - `echo "MENSAGEM"` para printar uma mensagem na tela
    - `echo $PATH` mostra onde procurar os binários para execução
    - `alias "COMANDO"` comandos para setar um "apelido" para um determinado comando, por exemplo executar um `ls -l` com apenas `ls`

- Comandos de manipulação de diretórios
    - Opções do comando `ls`
        - `ls` para listar arquivos e diretórios
        - `ls -a` opção `-a` serve para lista todos(all) arquivos, inclusive os arquivos ocultos que iniciam com um `.` no inicio do arquivo
        - `ls -l` opção `-l` serve para trazer mais informações sobre os arquivos.
        - `ls -h` opção `-h` serve para "humanizar" as informações, para deixar mais clara de leitura.
        - `ls -B` opção `-B` serve para não visualizar arquivos terminados com `~` no final do arquivo que simbolizam arquivos de backup.
        - `ls --color=auto` serve para diferenciar tipos de arquivos com cores
        - `ls -l PASTA -d` opção `-d` para mostrar detalhes de diretório
        - `ls -f` opção `-f` sem esse atributo a listagem de arquivos segue ordem alfabética, com o atributo `f` não.
        - `ls -F` opção `-F` com esse atributo a listagem segue ordem alfabética e com um separador entre diferentes tipos de arquivos.
        - `ls -g` opção `-g` oculta a coluna de dono dos arquivos
        - `ls -n` opção `-n` converte o nome e o grupo donos do arquivo para GUID e UUID que seria sua versão númerica.
        - `ls -L` opção `-L` oculta o tipo de arquivo com link simbólico
        - `ls -o` opção `-o` oculta a coluna de grupo dos arquivos
        - `ls -p` opção `-p` oculta o tipo de arquivo executável
        - `ls -t` opção `-t` lista os arquivos por data de criação mais recentes em primeiro
        - `ls -tr` opção `-tr` lista os arquivos por data de criação mais antigos em primeiro
        - `ls -X` opção `-X` lista os arquivos por extensão
        - `ls -R` opção `-R` lista de forma recursiva os arquivos e arquivos dentro de outros diretórios
    - Usos do comandos `cd`
        - `cd` para entrar em diretórios
        - `cd /home/USUARIO` - `cd` comando para mudar de diretório
        - `cd` somente comando `cd` ele entra no diretório do usuário que está logado
        - `cd -` colocando um `-` ele entra o último diretório acessado
        - `cd ~` como explicado o `~` simboliza o diretório home do usuário, então junto com o comando "cd" ele entra no diretório home do usuário.
        - `cd ..` Diretórios `.` e `..`. O `.` simboliza o diretório atual e o `..` simboliza o diretório anterior
        - `cd /` o `/` é o diretório "raiz" do Linux de onde se originam toda a ramificação de diretórios.
        - `cd /home/USUARIO` caminho absoluto, onde é descrito o caminho completo até o diretório ou arquivo desejado a partir do `/`
        - `cd USUARIO` caminho relativo, quando entramos em um diretório a partir de um em que estamos e não da raiz `/`
    - `pwd` mostra o diretório atual
    - Usos do comandos `mkdir`
        - `mkdir NOMEDAPASTA` para criar um diretório
        - `mkdir -p PASTA1 PASTA2` para criar mais de um diretório ao mesmo tempo
        - `mkdir -p PASTA1/PASTA1_1` para criar uma estrutura de diretórios sem que a raiz esteja criada
    - Usos do comandos `tree` 
        - `tree` comando para mostrar a "arvore" de diretórios
        - `tree - A` muda o formato apresentado pelo terminal
    - Usos do comandos `rmdir`
        - `rmdir` comando para apagar diretório vazios
        - `rmdir -p` comando para apagar arvore de diretórios vazios.
    - Usos do comandos `cat` e suas váriaveis
        - `cat NOMEARQUIVO` comando para visualizar conteúdo de um arquivo
        - `cat -n NOMEARQUIVO` comando para mostrar o número na frente de cada linha do conteúdo
        - `cat -s NOMEARQUIVO` junta e omite a apresentação de linhas em branco no arquivo
        - `cat -b NOMEARQUIVO` comando para mostrar o número na frente de cada linha do conteúdo somente em linhas que tenham conteúdo.
        - `cat -E NOMEARQUIVO` coloca um `$` ao final de cada linha para mostrar onde é seu final.
        - `cat -T NOMEARQUIVO` coloca um `ctrl+i` no lugar do tab.
        - `zcat NOMEARQUIVO.gz` para ver conteúdo de arquivos compactados com extensão `.gz`
        - `bzcat NOMEARQUIVO.bz2` para ver conteúdo de arquivos compactados com extensão `.bz2`
        - `xzcat NOMEARQUIVO.xz` para ver conteúdo de arquivos compactados com extensão `.xz`
        - `tac NOMEARQUIVO` mostra o conteúdo do arquivo do fim para o começo
        - `tac -s a NOMEARQUIVO` coloca uma letra "a" sempre que houver uma quebra de linha
    - Usos do comandos `rm`
        - `rm` comando sem atributos para excluir arquivos
        - `rm -r DIRETORIO` comando para excluir diretórios
        - `rm -rf` excluir arquivos e diretórios sem perguntar se tem certeza da exclusão
        - `rm -rf ARQUIVO1 ARQUIVO2` apagar vários arquivos ao mesmo tempo, sem perguntar.
        - `rm -rf *` apaga todos os arquivos e diretórios dentro do diretório onde está, menos arquivos ocultos
        - `rm -rf a*` apaga todos os arquivos iniciados com a letra "a"
    - Usos do comando `cp`
        - `cp` comando para copiar arquivos de lugar para o outro
            - `cp -l` copia arquivos criando hard links, espaço em disco continua o mesmo.
    - Usos do coamando `mv`
        - `mv` comando para mover arquivos de um lugar para outro

- Editores de texto no Linux
    - Nano
    - mcedit
    - vi (mais complexo)
    - vim (versão do vi com menos complexidade na edição de arquivos)

### Questões

1. Como remover um arquivo '-'?

:white_check_mark: rm '-'

:black_large_square: rm -f *dash*

:black_large_square: rm - --

:white_check_mark: rm -- -

---

2. Considerando a estrutura de Diretórios: _Diretorio17/Diretorio_17_1/Diretorio17_2/Diretorio_17_3/Arquivo.txt_, quando executar o comando `rmdir -p Diretorio17`, ele removerá com sucesso?

:black_large_square: Verdadeiro

:white_check_mark: Falso

---

3. Como tornar a cópia repetitiva de um diretório origem e destino mais rápida?

:black_large_square: Largar o Linux e instalar Windows, pois ele tem barra de progresso

:black_large_square: Upgrade de link de internet

:black_large_square: usar cp -f

:black_large_square: Trocar o HD por SSD

:white_check_mark: usar cp -u

---

4. Se voce precisa remover diretórios que contenham arquivos dentro, você usaria o rmdir?

:black_large_square: Verdadeiro

:white_check_mark: Falso

---

5. O comando 'rm -rf / data/arquivo.txt' é considerado um comando perigoso?

:black_large_square: O comando ignorarará / e removerá apenas o arquivo.txt

:white_check_mark: Sim, pois acidentalmente o usuário digitou um espaço entre o / e data, fazendo o rm -rf interpretar o argumento como 2 parametros (apagando o sistema de arquivos raíz). Felizmente distribuções novas pedem confirmação --no-preserve-root!

:white_check_mark: Sim, e vai apagar tudo em distribuições mais antigas que 2005

:black_large_square: O comando não é perigoso, vai deixar a máquina mais leve e com menos arquivos no disco

## Day 4

- Coringas e caracteres especiais
    - `*` 
        - `ls a*` mostra todos os arquivos iniciado com a letra "a"
        - `ls *path` mostra todos os arquivos que terminam com a palavras "path" no final
    - `?`
        - `ls a?` mostra arquivos que iniciam com a letra "a" e possuem apenas mais uma letra qualquer.
        - `ls a?t*` mostra arquivos que iniciam com a letra "a", tenham qualquer letra na segunda posição, tenha a letra "t" na terceira posição e o "*" para mostrar o resto.
    - `[a-z]`
        - `ls m[a-c]` mostra arquivos que iniciam com a letra "m" e que tenham as letras "a", "b" ou "c" no final.
    - `[^a-z]`
        - `ls m[^abc]` mostra arquivos que iniciam com a letra "m" e que não terminem com as letras "a", "b" ou "c" no final.
    - `{a}`
        - `ls x{zd,ze,zm}*` mostra arquivos que iniciam com a letra "x" e que tenham pedaços "zd", "ze" ou "zm" e que terminem com qualquer coisa.

- Comandos diversos
    - `clear` ou `CTRL + l` serve para "limpar" a tela
    - `#` colocando esse caractere no inicio do seu comando ele é salvo sem executar.
    - `date` comando para exibir informações de data e hora atual
        - `date -u` mostra data e hora UTC
        - `date -s HORA:MIN` seta uma hora manual no sistema
        - `date MESDIAHORAMINANOSEGUNDO` nesse formato ele atualiza data e hora do sistema
        - `hwclock --systohc` salva o horário definido na placa sem mudança ao reiniciar a maquina
        - `date +"%d-%m-%Y %T"` mostra em tela dia, mês, ano e a hora somente.
            - `%d` mostra o dia
            - `%Y` mostra o ano sem abreviação (2024)
            - `%y` mostra o ano abreviado (24)
            - `%j` mostra o número do dia do ano, por exemplo dia 250 do ano
            - `%T` mostra o horário completo
            - `%r` mostra o horário no formato 24h
            - `%p` mostra AM e PM
            - `date --date='@1'` mostra uma data especifica que aconteceu determinado contador, esse exemplo mostra a contagem do primeiro segundo contado pelo Unix (Quinta 01/01/1970 00:00:01)
        - `df` mostra o espaço livre no disco
            - `df -h` mostra em Megabytes do que em blocos, melhora a visualização
            - `df -H` mostra em blocos de 1000, impressão de HD maior
            - `df -l` mostra somente partições do sistema e omite pontos de montagem externo como um NFS, apresentados blocos de 1K
            - `df -m` mostra partições em blocos de 1M
            - `df -a` mostra todas as partições montadas, inclusive cgroups
            - `df -i` mostra os inodes livres
            - `df -T` mostra formato que estão formatada as partições
            - `df -Th -t ext4` mostra apenas partições formatadas em ext4
            - `df -P` mostra as partições em formato POSIX (Padrão)
        - `ln` comando para realizar links de arquivos
            - `ln -l` listar todos os links
            - `ln /bin/ls ls` cria um "hard" link do arquivo "/bin/ls" para um arquivo "ls" na pasta local (somente links para arquivos)
            - `ln -s /bin/ls ls-link` cria um link "simbólico" que seria só um apontamento para um arquivo original
        - `du` mostra o tamanho de cada arquivo no sistema
            - `du -H` mostra em formato humanizado em blocos de 1000
            - `du -h` mostra em formato humanizado em blocos de 1024
            - `du -hs` mostra em formato humanizado e sumariza os dados, no caso total de arquivos de um determinado diretório
            - `du -k` mostra em kbytes
            - `du -m` mostra em megabytes
            - `du --inodes` mostra o tamanho em inodes
            - `du -hc` mostra o total ao final do comando
        - `find` comando para procurar arquivos e diretórios no sistema
            - `find . -name ls` procura no diretório atual arquivos chamados de "ls"
            - `find . -type d -name mc` procura no diretório atual somente pastas chamadas "mc"
            - `find . -type f -name mc` procura no diretório atual somente arquivos chamados "mc"
            - `find . -maxdepth 2 -type f -name mc` procura no diretório atual e mostra arquivos chamados "mc" e desce no máximo 2 diretório na hierarquia
            - `find . -mindepth 2 -maxdepth 2 -type f -name mc` procura no diretório atual e mostra somente arquivos chamados "mc" e desce no máximo 2 e no mínimo 2 diretórios na hierarquia
            - `find . -mtime -1` mostra todos os arquivos que foram alterados a menos de 1 dia atrás
            - `find . -mtime +1` mostra todos os arquivos que foram alterados a mais de 1 dia atrás
            - `find . -amin -10` mostra todos os arquivos que foram alterados nos últimos 10 minutos
            - `find . -cmin -10` mostra todos os arquivos criados nos últimos 10 minutos
            - `find . -gid 1000` mostra todos os arquivos com gid 1000
            - `find . -user USUARIO` mostra todos os arquivos do USUARIO
            - `find . -links 5` mostra arquivos que estão tenha 5 links
            - `find . -size +1000` mostra arquivos de tamanho maior que 1000 blocos
        - `free` mostra espaço disponivel de memória ram no sistema
            - `free --kilo` mostra o espaço de memória ram em Kilobytes
            - `free --mega` mostra o espaço de memória ram em megabytes
            - `free --kibi` mostra o espaço de memória ram em blocos de 1024 kilobytes
            - `free --mibi` mostra o espaço de memória ram em blocos de 1024 megabytes
            - `free --mega -s 1` mostra o espaço de memória atualizado de 1 em 1 segundo
            - `cat /proc/meminfo` detalhes sobre memória ram
        - `grep` mostra pedaços de um arquivo ou conteúdo
            - `grep 'root' /etc/passwd` mostra as linhas que tenham a palavra "root"
            - `grep -v 'root' /etc/passwd` mostra as linhas que não tenham a palavra "root"
            - `grep -f ARQUIVO /etc/passwd` pesquisa o conteúdo de um arquivo no local pesquisado
            - `grep -i 'root' /etc/passwd` mostra as linhas que tenham a palavra "root ignorando letras maiúsculas e minúsculas"
            - `grep -E '^root.*nologin$' /etc/passwd` mostra as linhas, utilizando expressão regular, que inicia com a palavra "root e termine com "nologin"
            - `grep -F '.*' /etc/passwd` mostra as linhas que tenham caracteres especiais, ignorando caracteres de expressão regular
            - `grep -ri 'root' /etc/passwd` mostra as linhas que tenham a palavra "root" de forma recursiva em todos os arquivos
            - `grep -rih 'root' /etc/passwd` mostra as linhas que tenham a palavra "root" de forma recursiva em todos os arquivos, porém oculta o nome dos arquivos
            - `grep -ril 'root' /etc/passwd` mostra todos os arquivos tenham a palavra "root" porém oculta o conteúdo "root" e mostra só os arquivos onde a palavra aparece.
            - `grep -rin 'root' /etc/passwd` mostra o número da linha que tem a palavra "root" de forma recursiva em todos os arquivos.
        - `head` mostra as primeiras linhas de um arquivo, por padrão as 10 primeiras
            - `head -n 3 /etc/passwd` mostra as 3 primeiras linhas do arquivo
            - `head -c 50 /etc/passwd` mostra os primeiros 50 bytes do arquivo
        - `nl` numero a quantidade de linhas de um arquivo
            - `nl -f a -i 1 /etc/passwd` numera todas as linhas de forma sequencial
            - `nl -f a -i 2 /etc/passwd` numera todas as linhas pulando de 2 em 2
            - `nl -f a -i 1 -v 0 /etc/passwd` numera todas as linhas e especifica que a primeira linha será 0
        - `more` abre arquivos para visualização de forma paginada, para arquivos que não "cabem" na tela, somente é possível ir para o final do arquivo, não dá para subir.
        - `less` abre arquivos para visualização de forma paginada, para arquivos que não "cabem" na tela, diferente do `more` ele não mostra a porcentagem de visualização do arquivo e podemos utilizar as setas para subir e descer no arquivo. Podemos também pesquisar alguma palavra digitando o caractere `/PALAVRA` e damos um "enter" e a palavra será destacada se a palavra tiver mais de uma ocorrência dentro do arquivo podemos clicar a letra "n" para avançar a próxima palavra no texto.
        - `sort` ordena o conteúdo de um arquivo de forma do menor para o maior, primeiro números depois de A à Z.
            - `sort -r` reverte a ordenação do maior para o menor
            - `sort -n` ordena número de forma crescente
            - `sort -c` mostra se o arquivo está ou não ordenado
            - `sort +1` ordena o conteúdo pela segunda coluna
            - `sort +1 -t " "` ordena o conteúdo pela segunda coluna após o delimitador sendo um "espaço"
            - `sort -k 1` ordena o conteúdo pela segunda coluna pelo primeiro caractere como delimitador
        - `tail` comando para visualizar o conteúdo do final de um arquivo, padrão últimas 10 linhas
            - `tail -n 4 /etc/passwd` mostra as 4 últimas linhas do arquivo
            - `tail -f /var/log/auth.log` verifica em tempo real atualizações do arquivo
        - `time ls` o comando "time" na frente de outros comandos mostra o tempo de execução de um determinado comando
        - `touch ARQUIVO` cria um arquivo vazio
            - `touch -t 07150830` altera a data de criação do arquivo, padrão (MM-DD-HH-MI)
            - `touch -a -t 07150830` altera a data do último acesso do arquivo, padrão (MM-DD-HH-MI)
        - `uptime` tempo de atividade da maquina
        - `dmesg` mostra mensagem do kernel da maquina
            - `dmesg -t` oculta a coluna de timestamp (primeira coluna)
            - `dmesg --color=never` para mostrar o comando somente em preto e branco ou na cor padrão do sistema.
            - `dmesg -w` mostra em tempo real mensagens de atualização do Kernel, parecido com o comando `tail -f`
            - `dmesg -x` mostra algumas informações de forma mais legivel ao humando, parecido com a opção `-h` em alguns comando anteriores
            - `dmesg -T` mostra o Timestamp de uma forma mais legivel ao humano
            - `dmesg -c` mostra todas as mensagens do Kernel e limpa o conteúdo, se executar o comando novamente não terá resultado
        - `mesg` aplicativo para mandar mensagens pelo terminal para outros usuários
        - `echo "MENSAGEM"` mostra mensagens na tela do terminal
            - `echo -n "MENSAGEM"` mostra mensagens na tela do terminal sem quebra de linha
            - `echo -e "MENSAGEM"` mostra mensagens na tela do terminal interpretando caracteres especiais



