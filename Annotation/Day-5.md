# LPI Essentials - LinuxTips

## Day 5

- Continuação em comandos diversos
    - `chattr` altera atributos de um arquivo
        - `chattr +i ARQUIVO` "i" de imutável protege o arquivo contra deleção e alteração
        - `chattr +i DIRETORIO` "i" de imutável adiciona a proteção de deleção e alteração em um diretório incluindo seus arquivos
        - `chattr -i ARQUIVO` remove a proteção adicionada anteriormente contra deleção
        - `chattr -R -i DIRETORIO` remove a proteção adicionada anteriormente contra alteração de forma recursiva
        - `chattr +a ARQUIVO` "a" de "append", permite somente adição de conteúdo ao arquivo, com o comando `echo "TEXTO" >> ARQUIVO` que adiciona linhas ao final de um arquivo
        - `chattr +a DIRETORIO` "a" de "append", em diretórios com esse atributo ativo ele impede a deleção de arquivos da pasta
        - `chattr =ai *` insere os atributos "a" e "i" a todos os arquivos
        - `chattr +c` "c" de compactado, ele é compactado no momento da inicialização do Kernel
        - `chattr +s` "s" de seguro, para deleção segura do arquivo
        - `chattr +S` "S" de sync, para realizar uma gravação de arquivos de forma automatica no sistema
        - `chattr +D` "D" de diretório, para realizar uma gravação de diretórios de forma automatica no sistema
        - `chattr +d` "d" de dump, faz que os arquivos e diretórios não sejam incluidos no backup dump
    - `lsattr` lista atributos de um arquivo
        - `lsattr DIRETORIO -d` mostra os atributos do diretório
    - `cut` comando para cortar e mostrar uma parte do conteúdo
        - `cut -d ":" -f 1 /etc/passwd` serve para mostrar a 1º coluna, tendo o delimitador ":"
        - `cut -d ":" -f 1-3 /etc/passwd` serve para mostrar os 3 primeiros valores/palavras, tendo o delimitador ":"
        - `cut -d ":" -f 1,5 /etc/passwd` serve para mostrar o 1º e o 5º valor/palavra, tendo o delimitador ":"
        - `cut -b 1-5 /etc/passwd` serve para mostrar os 5 primeiros bytes do arquivo (não conta espaço)
        - `cut -c 1-5 /etc/passwd` serve para mostrar os 5 primeiros caracteres do arquivo
    - `cmp ARQUIVO1 ARQUIVO2` comando para "comparar" arquivos, se os arquivos foram iguais não apresenta nada em tela, caso seja diferentes ele apresenta a quantidade de bytes diferentes.
        - `cmp -s ARQUIVO1 ARQUIVO2` caso os arquivos sejam diferentes com o argumento "s" ele não apresenta nada em tela. O comanda guarda um código de retorna na váriavel `echo $?`
    - `diff ARQUIVO1 ARQUIVO2` comando para mostrar diferenças entre arquivos, ele mostra de forma mais humana a diferença entre os arquivos, mostrando o conteúdo que tem em um arquivo e em outro não
        - `diff -u ARQUIVO1 ARQUIVO2` ele faz um detalhamento, de forma mais humana, as diferenças entre os arquivos.
        - `diff -ru ARQUIVO1 ARQUIVO2` ele faz um detalhamento, de forma mais humana, as diferenças entre arquivos dentros de pasta
    - `whereis ls` procura uma página de manual de alguma aplicativo, nesse caso do comando `ls`
    - `which ls` procura onde está o localizado o binário do aplicativo

- Curiosidade, aplicativo `patch`
    - O comando `patch` serve para aplicar "patchs" de mudança, utilizando a saída do comando `diff` deixando os arquivos iguais ou desfazendo mudanças que foram aplicadas.
        - `patch -p1 -N </DIRETORIO/PATCH>` para aplicar as alterações contidas do resultado do comando `diff` nos arquivos nas pastas de nível abaixo
        - `patch -p1 -R </DIRETORIO/PATCH>` para reverter as alterações contidas do resultado do comando `diff` nos arquivos nas pastas de nível abaixo

- Gerenciamento e execução de processos
    - `ps` de "process" mostra os processos em execução no sistema dentro do shell, cada comando gera um processo
        - uma pasta com o número do PID é criada dentro de `/proc/`
        - `ps | grep vim` mostra processos do aplicativo "vim" em execução
        - `ps -a` "a" mostra todos os processos em execução em todos os terminais que estiverem abertos
        - `ps -ax` "x" mostra todos os processos em execução de usuários logados e usuários de sistema
        - `ps -axu` "u" mostra todos os processos em execução de usuários logados e usuários de sistema e mostra o usuário que está executando cada processo.
        - `ps -axm` "m" mostra o uso de memória por cada processo
        - `ps -axf` "f" mostra os processos em execução em forma de arvore
        - `ps -axe` "e" mostra as variaves de ambiente que o comando está utilizando
        - `ps -axew` "w" se um processo não mostrar a linha completa o "w" é usado para realizar uma quebra de linha e mostrar toda a linha do processo.
        - `ps -ax --sort=pid` para ordenar os processos pelo número do PID
    - `pidof cron` mostra o número do PID de algum processo pelo nome
        - `pidof -s cron` mostra somente o primeiro PID caso o processo tenha mais de um
    - `pstree` mostra os processos em forma de arvore
        - `pstree -A` mostra os processos em forma de arvore de forma diferente
        - `pstree -c` mostra os processos em forma de arvore incluindo os processos "pais"
        - `pstree -h` mostra os processos em forma de arvore destacando os processos "pais"
        - `pstree -p` mostra os processos em forma de arvore mostrando também o número dos PIDs
        - `pstree -p -H 352` mostra os processos em forma de arvore mostrando também o número dos PIDs e destaca o número do PID especificado
        - `pstree -p -H 352 -u` mostra os processos em forma de arvore mostrando também o número dos PIDs e destaca o número do PID especificado e mostra o UID do processo (usuário)
        - `pstree -p -H 352 -g` mostra os processos em forma de arvore mostrando também o número dos PIDs e destaca o número do PID especificado e mostra o GID do processo (grupo)
    - `kill` comando para matar processos
        - `kill NUMEROPROCESSO` encerra um processo pelo número do PID
        - `kill -15 1234` ou `kill -TERM 1234` encerra um processo de forma "amigável"
        - `kill -9 1234` ou `kill -KILL 1234` encerra um processo de forma "forçada"
        - `kill -1 1234` ou `kill -HUP 1234` efetua uma releitura dos arquivos de configuração sem encerrar o processo
        - `kill %1` encerra um processo pelo número do Job em execução em background
    - `pgrep` faz um filtro de processos
        - `pgrep -u root sshd` mostra o PID de todos os processo do usuário root com o nome de "sshd"
        - `pgrep sshd` mostra o PID dos processo com o nome de "sshd"
    - `pkill` encerra processo pelo nome do processo
        - `pkill -u USUARIO sleep` encerra o processo que está rodando com o usuário "USUARIO" e com o nome de "sleep"
    - `killall` encerra processo pelo nome do processo
        - `killall -u USUARIO sleep` encerra o processo que está rodando com o usuário "USUARIO" e com o nome de "sleep"
    - `killall5` mata todos os processo da maquina, só roda como superusuário
        - `killall5 -9` mata todos os processos da máquina
    - `nohup` protege processos em execução que eles recebem sinais de encerramento como o "-9" e o "-15"
        - `nohup sleep 100 &` protege o comando `sleep` de ser encerrado
    - `top` mostra a execução dos processo em tempo real, parecido com o gerenciador de processos do Windows.
        - Quando o comando `top` está em execução se apertar a tecla "M" muda a visualização de memória
        - Quando o comando `top` está em execução se apertar a tecla "1" muda a visualização de CPU
        - Quando o comando `top` está em execução se apertar as teclas "SHIFT + M" muda a visualização para os processos que estão tendo mais consumo de memória em primeiro
        - Quando o comando `top` está em execução se apertar a tecla "F" você pode escolher por qual atributo que quer que seja ordenado
        - Quando o comando `top` está em execução se apertar a tecla "K" você pode escolher encerrar processos pelo PID
        - Quando o comando `top` está em execução se apertar a tecla "D" você pode mudar o delay que é atualizado o top, padrão 3 segundos
        - Quando o comando `top` está em execução se apertar as teclas "SHIFT + W" você salva a customização que tenha feito para o comando `top`
        - `top -i` ignora processos Zumbi
        - `top -c` mostra a linha inteira do comando que está em execução
    - `nice` comando para colocar prioridade a uma execução. Padrão é 0. as prioridades vão de -20 até 19.
        - `nice -n 10 sleep 100` seta prioridade 10, menos do que 0
        - Para setar prioridade negativas, que são de maior prioride somente com superusuário
        - `renice -n 10 -p 123` coloca uma nova prioridade (10) para o PID 123
        - `renice -n 10 -u USER` coloca uma nova prioridade (10) para os processos rodando pelo usuário "USER"
        - `renice -n 10 -g GROUP` coloca uma nova prioridade (10) para os processos rodando pelo grupo "GROUP"
    - `tload` comando para verificar consumo de CPU em tempo real.
    - `vmstat` comando para verificar o tempo de execução e recursos que um processo está usando
    - Váriavel `$PATH` onde é guardado os caminhos onde estão localizados os binários do sistema
    - `&` utilizado ao final de um comando ou aplicativo faz ele "rodar" em segundo plano
        - `sleep 10 &` nesse exemplo ao invés de segurar a tela por 10s ele "roda" em segundo plano. Ao final da execução do comando é gerado um retorno de sucesso ou não da execução
    - `jobs` para verificar comando que estão em execução em segundo plano
    - `fg 1` "foreground" para trazer o primeiro comando que está em execução novamente para o primeiro plano
    - Após executar um comando para colocar ele em background, primeiro é necessário digital "CTRL + Z" para parar o processo depois executar o comando `bg 1` que no caso "joga" o processo que estava parada novamente para execução agora em background.
    - Para cancelar um processo em segundo plano
        - Trazer novamente ele para primeiro plano com o comando `fg 1` e depois digital "CTRL + C"
        - Outra forma é utilizando o comando `kill %1`, 1 seria o número do serviço.
    - `;` utilizado para executar mais de um comando. Ex: `ls ; tree ; sleep 1` os comandos separados por ";" serão executados em sequência.
    - 

- Curiosidades
    - `sleep` comando para aguardar somente
        - `sleep 10` comando para "segurar" o terminal por 10s

- Multiplexador de terminais
    - `screen` cria novas telas em um mesmo terminal, parecido como você apertar um "ALT + TAB" no Windows, porém você pode deixar algum processo em execução e consegue entrar nessa "screen" novamente para continuar o processamento
    - `tmux` cria novas telas em um mesmo terminal, parecido como você apertar um "ALT + TAB" no Windows, porém você pode deixar algum processo em execução e consegue entrar nessa "screen" novamente para continuar o processamento 


### Questões

1. Quais atributos sao usados impedir a remoção de arquivos em um diretório pelo usuário root?

:black_large_square: Nenhum, o root possui acesso irrestrito a arquivos e pastas

:white_check_mark: a

:black_large_square: D

:black_large_square: d

:white_check_mark: i

--- 

2. Quais atributos sao usados impedir qualquer alteração e remoção de arquivos, mesmo pelo usuário root?

:black_large_square: Nenhum, o root possui acesso irretrito a arquivos e diretórios

:white_check_mark: i

:black_large_square: a

:black_large_square: D

:black_large_square: d

---

3. Diff pode ser usado para comparar binários

:black_large_square: verdadeiro

:white_check_mark: falso

---

4. Que comando é usado para salvar diferença entre dois diretórios?

:black_large_square: diff diff1/ diff1/

:black_large_square: diff -ru diff1/ diff2/ --save diferencas.diff

:white_check_mark: diff -ru diff1 diff2 >diferencas.diff

:black_large_square: diff -ru diff1 >diferencas.diff /diff2

:black_large_square: diff -ru diff1 diff2

---

5. Para aplicar corretamente um arquivo contendo as diferenças salvas pelo diff geradas em uma pasta em nível anterior?

:black_large_square: patch <../diferencas.diff

:white_check_mark: patch -p1 -N <../diferencas.diff

:black_large_square: patch -p0 <../diferencas.diff

:black_large_square: patch <../diferencas.diff -p1 -N

---

6. Qual dos comandos abaixo, quando executado no Linux, "pode" fazer voce ir até a empresa para reestabelecer um servidor inacessível (caso ele seja físico e não tiver iDRAC/iLO)?

:black_large_square: pkill

:black_large_square: killall

:white_check_mark: killall5

:black_large_square: ps -e kill

---

7. Que atalho do comando top permite exibir a linha de comando completa dos processos em execução/

:white_check_mark: c

:black_large_square: q

:black_large_square: f

:black_large_square: Shift + M

---

8. CTRL + B é a combinação de teclas usadas no tmux para gerenciar os terminais

:white_check_mark: Verdadeiro

:black_large_square: Falso