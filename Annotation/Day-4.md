# LPI Essentials - LinuxTips

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
        - `su` comando para elevar permissionamento para root
            - `su -` ou `su -l` eleva as permissões para root eliminando váriaveis de ambientes configuradas anteriormente
            - `su - www-data -s /bin/bash` para especificar um usuário para logar em um determinado shell
        - `sudo` comando para elevar permissionamento para root, podendo especificar grupos que podem realizar tal ação (sudoers)
            - `sudo id` executa o comando `id` como root sem alterar o usuário
            - `sudo su` executa o comando `su` como root e automaticamente já se loga como root
        - `adduser USUARIO sudo` comando para adicionar um usuário comum ao grupo de root
        - `deluser USUARIO sudo` comando para remover um usuário comum ao grupo de root
        - `groups` mostra os grupos que um usuário faz parte
        - `sync` força a gravação do buffer no disco, por padrão o sistema faz a gravação a cada 10/20 segundos
        - `uname` comando para mostrar o kernel da máquina
            - `uname -a` mostra detalhes do sistema operacional, como versão do Kernel.
            - `uname -s` mostra o Kernel que está sendo utilizado
            - `uname -n` mostra o nome da máquina
            - `uname -r` mostra a versão do Kernel atual
            - `uname -v` mostra a data que o kernel foi compilado
            - `uname -m` mostra a arquitetura utilizado pelo sistema
        - `hostname` mostra o nome da máquina
        - Comandos para reiniciar a máquina
        - `shutdown --help` para opções detalhadas para reiniciar ou desligar a máquina
            - `reboot`
            - `reboot -f` reinicar de forma forçada
            - `systemctl reboot`
            - `shutdown -r now`
                - `shutdown -r +30 "Mensagem"` para programar um reboot da maquina e mandar uma mensagem aos usuários que estiverem logados.
            - `echo b > /proc/sysrq-trigger` outra maneira para reiniciar de forma forçada
            - `init 6`
        -  Comandos para desligar a máquina
            - `halt`
            - `systemctl halt`
            - `shutdown -h now`
                - `shutdown -h 18:00` para programar o desligamento para as 18h.
                - `shutdown -h +30` para programar de desligar a maquina daqui 30 min
                - `shutdown -c` para cancelar o agendamento
            - `poweroff` para desligar
            - `echo o > /proc/sysrq-trigger` maneira para desligar de forma forçada
            - `init 0`
        - `wc` "word count" mostra detalhes de um arquivo, como a quantidade de caracteres, a quantidade de palavras e de linhas
            - `wc -l` conta somente o número de linhas
            - `wc -c` conta somente o número de bytes
            - `wc -w` conta somente o número de palavras
        - `seq` mostra uma sequência numérica no terminal
            - `seq 10` mostra uma sequência de 1 à 10
            - `seq 2 10` mostra uma sequência iniciando do número 2, de 2 à 10
            - `seq 2 2 10` mostra uma sequência iniciando do número 2, pulando de 2 em 2 até o número 10
            - `seq -w 10` mostra a mesma sequência mas com 0 na frente, 01, 02 e etc

### Questões

1. Que comando permite ordenar um arquivo?

:black_large_square: head

:black_large_square: tail

:white_check_mark: sort

:black_large_square: hardlink

:black_large_square: ln

---

2. Que comandos permitem numerar as linhas de um arquivo?

:black_large_square: ln

:white_check_mark: nl

:black_large_square: cat

:black_large_square: wc

:white_check_mark: cat -n

---

3. Qual dos comandos abaixo não permite reiniciar o sistema?

:black_large_square: shutdown -r now

:black_large_square: reboot

:black_large_square: reboot -f

:black_large_square: echo b >/proc/sysrq-trigger

:white_check_mark: echo r >/proc/sysrq-trigger

---

4. Qual a opção usada no sysrq-trigger para desligar (halt) a máquina?

:white_check_mark: o

:black_large_square: h

:black_large_square: r

:black_large_square: p